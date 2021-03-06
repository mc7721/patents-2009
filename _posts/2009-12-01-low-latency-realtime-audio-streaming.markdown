---

title: Low latency real-time audio streaming
abstract: Systems and methods for audio streaming in a computing device are described. In one aspect an interface to an adapter driver is provided. The adapter driver is associated with an audio device. The adapter driver and a wave real-time (WaveRT) port driver associated with the computing device use the interface to configure direct access by a client of the computing device and by the audio device to a cyclic buffer. The direct access is for rendering and/or capturing an audio stream. The direct access is independent of any copying by a port driver on the computer system of the audio stream to any buffer.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08078302&OS=08078302&RS=08078302
owner: Microsoft Corporation
number: 08078302
owner_city: Redmond
owner_country: US
publication_date: 20091201
---
This application is a continuation of and claims priority from U.S. patent application Ser. No. 10 956 280 titled Low Latency Real time Audio Streaming filed on Oct. 1 2004 and hereby incorporated by reference.

Systems and methods for audio streaming in a computing device are described. In one aspect an interface to an adapter driver is provided. The adapter driver is associated with an audio device. The adapter driver and a wave real time WaveRT port driver associated with the computing device use the interface to configure direct access by a client of the computing device and by the audio device to a cyclic buffer. The direct access is for rendering and or capturing an audio stream. The direct access is independent of any copying by a port driver on the computer system of the audio stream to any buffer.

Audio devices that utilize standard wave port drivers such as WaveCyclic and WavePci drivers typically require constant attention from the driver to service an audio stream after it enters the run state. For instance to accommodate the needs of various DMA engines e.g. unorthodox buffer alignment requirements limited address range inability to handle a contiguous buffer of arbitrary length or a sample split between two memory pages etc. conventional port drivers give an audio device supplied miniport driver the ability to allocate its own cyclic buffer. The conventional port drivers then copy data at regularly scheduled intervals from an audio buffer into the allocated miniport buffers. The regularly scheduled intervals are a function of a timing window which is configured to be wide enough to contain the processing cycles needed to copy the data and then made even larger to accommodate any unforeseen delays and or timing tolerances in the underlying software scheduling mechanism.

Unfortunately such driver copying of audio data from a first audio buffer into a second miniport buffer associated with an audio device introduces audio stream processing latency. This introduced latency increases as the width of the timing window increases. Such processing latencies are substantially incompatible with real time and low latency audio applications possibly resulting in poor audio rendering and capture performance.

Another problem with conventional audio port drivers such as the WavePci port driver is that it uses miniport drivers to perform complex operations that can lead to synchronization errors and other timing problems. For example a WavePci miniport driver cannot hold its own spin lock when it calls into a port driver to obtain or release mappings. Thus the miniport driver can not assume that it has exclusive access to any shared data structures that rely on the spin lock to serialize accesses. An additional problem is that the miniport driver has to be configured to revoke mappings at any time during stream playing. For instance cancellation of an I O request packet carrying audio data causes the port driver to revoke the unprocessed mappings in the IRP. Failure to perform these operations correctly leads to synchronization errors and other timing problems that may negatively effect an audio application.

To make matters worse a WavePCi miniport driver continually obtains and releases mappings during the time that the stream is running. Though this is not as onerous as the data copying overhead described above the software overhead of handling mappings in such a manner introduces additional audio stream processing latencies which in turn reduces audio application performance.

In view of the above systems and method without the above discussed problems are desired to enhance real time audio streaming performance.

WaveRT port driver solves the latency performance problems of standard audio port drivers by providing a client e.g. global audio engine and component s associated with audio device with direct access to cyclic buffer for real time rendering of an audio stream and or real time capture of an audio stream . Such direct access eliminates among other things copying operation s of conventional systems that need to copy an audio stream from a render buffer to audio device specific buffer s and eliminates the need for audio device miniport drivers to synchronize access to any data structures that may be shared with port class system driver component s . More particularly after global audio engine has mixed playback audio stream s from an executing audio application and subsequently written the mixed audio stream into cyclic buffer audio device pulls audio stream from cyclic buffer for playing independent of any copying by WaveRT port driver of audio data to any buffer associated with the audio device. WaveRT port driver further reduces latency of rendering and or capturing audio stream s by leveraging real time scheduling support of OS and or utilizing hardware innovations such as the low latency isochronous transfer modes of PCI Express devices to complement OS real time scheduling.

To achieve these ends WaveRT port driver supports client e.g. global audio engine setting of a pin to a run state which allows the client to begin moving audio stream directly to or from the cyclic buffer . Thus and in contrast to conventional port drivers WaveRT port driver does not use the data transport facilities in kernel streaming KS to play or record audio. This avoids degraded performance associated with data transport facilities in KS which include for example performance degradation cause by transitions between user mode application space and kernel mode driver space for each I O request blocking while waiting for completion of an I O request use of CPU cycles necessary to copy audio data into a miniport supplied buffer etc.

At block the registered WaveRT miniport driver in turn provides registration information to port class system driver regarding a rendering or capture device that represent a respective audio device . Such registration information is shown as a respective portion of other data of . In this implementation the registration information corresponds to a KS filter which is registered under one of KSCATEGORY RENDER or KSCATEGORY CAPTURE categories respectively. Next at block a client such as global audio engine enumerates the registered registration information to select and instantiate a real time audio device represented by a respective KS filter s . The instantiated KS filter s has the following components 

At block it is determined if KS filter s performs audio rendering. If so procedure continues at block wherein the global audio engine or other client program module specifies or opens a playback stream as follows 

The global audio engine opens a pin on the KS filter s and the WaveRT miniport driver creates the pin instance. While opening the pin the global audio engine passes the stream s wave data format to the WaveRT miniport driver . The miniport driver uses this information to select a proper size for cyclic buffer

The audio engine requests a cyclic buffer of a particular size from the WaveRT miniport driver e.g. with KSPROPERTY RTAUDIO BUFFER property etc. see paragraph 0039 and on . Responsive to this request the WaveRT miniport driver allocates cyclic buffer . If the hardware audio device cannot stream from cyclic buffer of the requested size the WaveRT miniport driver allocates a cyclic buffer that comes as close as possible to this requested size while satisfying the hardware constraints and system resource limitations. WaveRT miniport driver maps cyclic buffer into the hardware s DMA engine shown as component of . Port class driver makes cyclic buffer accessible to global audio engine in user mode.

At block global audio engine schedules a real time thread to periodically write audio stream to the cyclic buffer . Audio application s provide the audio stream for rendering. At block if the audio device does not provide direct support for looped buffers the miniport driver periodically reprograms the audio device . The resulting configuration supplies glitch free audio on audio hardware that either supports looped buffers or uses a real time thread to regularly update the hardware.

At block if it is determined that KS filter s performs audio capture recording procedure continues at block wherein the global audio engine or other client program module opens a capture stream as follows 

The miniport driver might have to allocate a cyclic buffer that is bigger or smaller than the requested size e.g. buffer alignment size requirements of hardware depending on the hardware restrictions and available system resources. To ensure that the buffer is accessible to the audio hardware e.g. a microphone such as that shown in the miniport driver uses memory a respective portion of program data accessible to WaveRT port driver to allocate the cyclic buffer .

WaveRT port driver maps the allocated cyclic buffer into a contiguous block of virtual memory that the user mode client can access. Miniport driver maps the entire allocated buffer into the DMA hardware buffer queue.

At block Miniport driver performs workarounds if any to configure the hardware to cycle through the buffer. For example if a chipset does not support buffer looping in hardware miniport driver updates a single hardware register periodically which is done in either an interrupt service routine ISR or a real time thread. The consumption of processing resources by this operation is minimal

In write position is the location just past a last audio sample piece of data that the client wrote to the buffer . Play position is a piece of data sample that the audio device is currently playing. Write and play positions continually progress from left to right as audio stream flows through buffer . When the write or play position reaches the end of buffer it wraps around to the start of buffer .

The latency from the time that client writes an audio sample a portion of audio stream to buffer until the audio device plays it is the separation between write position and play position . In this example this separation is the sum of the following two sources of latency marked as A and B in 

Client has no control over latency A which depends entirely on the hardware. A typical FIFO might store enough samples to feed the DAC for roughly 64 ticks of the sample clock. However client does control latency B. Making latency B too large introduces unnecessary delays into the system however making it too small risks starving the audio device. By scheduling a real time thread to update buffer client can make the latency smaller than would otherwise be practical.

To determine how small the separation between the write and play positions is without risking FIFO starvation underflow conditions client considers hardware delays that audio stream encounters from the time that client writes audio stream to cyclic buffer until audio stream is played by device .

After calculating how much separation to maintain between the write and play positions client monitors the play position at regular time intervals to determine how far to advance write position . At the start of each interval client writes enough audio stream data to cyclic buffer to keep the hardware busy through the start of the next time interval. One way to obtain play position is through the KSPROPERTY AUDIO POSITION property request which is part of API but each request requires a transition between user mode and kernel mode. In this implementation PortCls supports a KSPROPERTY RTAUDIO POSITION REGISTER property request which provides a more efficient means for obtaining play position . If the audio hardware contains a position register that points to the play position the property request maps the register into a virtual memory address that is accessible to the user mode client . Thereafter the client simply reads the current value of the register from this address and no kernel mode transition is required.

The role of the WaveRT port driver is minimal while an audio recording stream remains in the run state. As shown in the audio device captures the audio stream and writes it to the cyclic buffer and then the client reads the audio stream from the buffer . This activity requires no intervention e.g. no audio data copying by the driver. also identifies the record or write position as the buffer location of the sample that the audio device is currently recording e.g. capturing from a microphone through an analog to digital converter or ADC . Note that the write position is the future buffer location into which the audio device will write the sample after it passes through the FIFO . The read position is the next sample that the global audio engine will read from the buffer . The record and read positions continually progress from left to right as the audio stream flows through the buffer . When the record or read position reaches the end of the buffer it wraps around to the start of the buffer.

The latency from the time that the audio device captures an audio sample in the ADC until the client reads it is simply the separation between the record position and read position. This separation is the sum of the following sources of latency marked in this example as A and B 

The client has no control over latencies A and C because they depend on the hardware audio device . A typical FIFO might store roughly 64 samples from the ADC. However the client does control latency B. Making latency B too large introduces unnecessary delays into the system. By scheduling a real time thread to read the buffer the client can make the latency smaller than would otherwise be practical.

To determine how small the separation between the read and record positions is made without causing glitches the client considers any hardware delays that the data encounters from the time that the audio device captures the audio stream until the client reads the audio stream from the cyclic buffer . In addition to the delay through the audio device s internal FIFO other hardware delays might exist. For example packet based hardware interfaces such as PCI Express introduce transport delays from the time that the hardware device initiates a write operation until the data appears in main memory. The client can obtain a summary of these delays by sending a KSPROPERTY RTAUDIO HWLATENCY property request to miniport port driver . KSPROPERTY RTAUDIO HWLATENCY property request is part of API . The client can obtain a summary of the delays by sending a KSPROPERTY RTAUDIO HWLATENCY property request to WaveRT port driver .

After calculating how much separation to maintain between the record and read positions client monitors the record position at regular intervals to determine how much the read position lag. During each interval the client reads only the data that the audio device is certain to have already written to the buffer. The client can obtain the current record position through either a KSPROPERTY AUDIO POSITION or KSPROPERTY RTAUDIO POSITIONREGISTER property request via API which is exposed by WaveRT mini port driver . In this implementation the latter is more efficient because it allows the client to read the record position directly without incurring the cost of a kernel mode transition.

This section presents guidelines for writing WaveRT miniport driver s and designing audio hardware that is WaveRT compatible.

A WaveRT miniport driver provides an implementation of the IMiniportWaveRTStream GetHardwareLatency method. This method supports the KSPROPERTY RTAUDIO HWLATENCY property.

A WaveRT miniport driver automatically reports FIFO overruns and underruns. This feature is helpful in detecting glitches in the audio stream during testing of the audio device and driver software.

For new designs hardware implementers design DMA channels for their audio devices to support the following features 

Note that the WaveRT port driver supports existing hardware designs that lack the ability to perform scatter gather transfers or automatic buffer looping. If an audio device lacks scatter gather capability the WaveRT miniport driver allocates cyclic buffers consisting of pages that are physically contiguous in memory. If an audio device lacks automatic buffer looping WaveRT miniport driver intervenes when the DMA channel reaches the end of the cyclic buffer by configuring the DMA channel to begin transferring data at the beginning of cyclic buffer .

For new designs hardware implementers include a position register for each DMA channel the audio device provides the DMA channel . A position register indicates the current buffer position as a byte offset from the beginning of cyclic buffer . The position register reading is zero at the beginning of the buffer. When the position register reaches the end of the cyclic buffer it automatically wraps around to the beginning of the buffer resets to zero and continues to increment as the buffer position advances. Position registers are mapped to virtual memory so that clients can read the registers directly.

In one implementation position registers indicate the buffer position of the audio data samples that are currently moving through the audio device s digital to analog and analog to digital converters DACs and ADCs . However this information might not be directly available from an audio chip set that divides the digital and analog functions into separate bus controller and codec chips. Typically the position registers are located in a bus controller chip and each register indicates the position of the audio stream that the controller is writing to or reading from codecs. After obtaining a reading from this type of position register the client can estimate the current position of the samples that are moving through the DACs or ADCs by adding or subtracting the delay through a codec. A client obtains the codec delay from the KSPROPERTY RTAUDIO HWLATENCY property request. For this reason a WaveRT miniport driver accurately reports the codec delay when the port driver calls the IMiniportWaveRTStream GetHardwareLatency method in response to this type of property request.

Note that the WaveRT port driver supports existing hardware designs that lack position registers . For a device with this limitation the WaveRT miniport driver purposefully fails calls to the IMiniportWaveRTStream GetPositionRegister method which forces the port driver to fail KSPROPERTY AUDIO GETPOSITIONREGISTER property requests. In this case clients obtain the current position through the KSPROPERTY AUDIO GETPOSITION property which incurs the overhead of a transition between user mode and kernel mode for each position reading.

In one implementation a WaveRT compatible audio device includes a clock register a useful hardware feature. Audio application programs can use clock registers to synchronize audio streams in two or more independent audio devices that have separate and unsynchronized hardware clocks. Without clock registers an application is unable to detect and compensate for the drift between the hardware clocks.

The sample clock that the audio hardware uses to clock audio data through the digital to analog or analog to digital converters be derived from the internal clock that increments the clock register. A clock register that increments at a rate that is asynchronous with respect to the sample clock is of no use for synchronization and not be exposed. Similar to the position registers the clock register is mapped to virtual memory so that clients can read the register directly.

User mode software e.g. clients does not directly alter the state of any hardware register and does not read any registers other than the clock register and position registers . To these ends hardware designers mirror the clock register and position registers into a separate memory page or pages that are mapped to the client s virtual address space. This page mirror none of the audio device s other hardware registers. In addition the hardware restricts accesses of the clock and position registers in the mirrored page to read only.

A WaveRT miniport driver never need to touch the audio stream in an audio device s cyclic buffer . As discussed previously the hardware is designed so that audio stream flows directly between the client and audio hardware with no intervention by the audio driver software . However OS provides two means to perform software processing of audio data without violating this rule 

Audio processing objects APOs APOs perform generic audio processing functions for example equalization that are not specific to a particular audio device. An APO processes an audio stream from an application before that stream is added to the global mix Global GFX effects filters GFX filters perform hardware specific processing of an audio stream. A GFX filter is tied to a particular audio device by the .inf file that installs the device. The effect of a GFX filter is global because it affects the global mix that plays through the audio device. For purposes of illustration such APOs and GFX filters are respective portions of other program module s or other data of .

Global mixing is performed by the global audio engine which is the user mode system component that is responsible for mixing the audio streams from audio application s . Typically the global audio engine is the client that directly exchanges data with the WaveRT audio device through the cyclic buffer .

When a user enables an APO the system inserts the APO into one of the global audio engine s input streams. When the user enables a GFX filter the system inserts that filter into the output stream from the global audio engine. The global audio engine executes all enabled APOs and GFX filters synchronously a before performing global mixing the engine runs the APOs on the input streams and b after performing global mixing the engine runs the GFX filters on the output stream. This scheme eliminates all the scheduling uncertainties that would result from scheduling the APOs and GFX filters as separate threads. Thus the contribution of APOs and GFX filters to audio stream latency reduces simply to their execution times.

This section describes exemplary interfaces properties and structures that are used by the WaveRT port driver and WaveRT miniport driver . The WaveRT port driver and miniport driver communicate with each other through four primary device driver interfaces respectively encapsulated by APIs or .

IPortWaveRTStream A stream specific interface providing helper functions that the WaveRT miniport driver calls to perform allocation and mapping of cyclic buffers.

The IPortWaveRT interface is the main interface that the WaveRT port driver exposes to the adapter driver that implements the WaveRT miniport driver object . An adapter driver creates an IPortWaveRT object by calling PcNewPort and specifying REFIID IID IPortWaveRT. IPortWaveRT inherits from the IPort interface. GUID constant IID IPortWaveRT is defined in header file portcls.h.

An adapter driver see other program modules forms a port miniport driver pair by binding an IPortWaveRT object to an IMiniportWaveRT object. The PortCls system driver registers this pair with the system as a real time wave filter s .

IPortWaveRT inherits the methods in the IPort interface. In this implementation it provides no additional methods.

The IPortWaveRTStream interface is an audio stream specific interface that provides helper methods for use by the WaveRT miniport driver . The miniport driver calls these methods to perform allocation and mapping of cyclic buffers for audio data . The WaveRT port driver implements this interface. The port driver gives an IPortWaveRTStream object reference to each miniport driver stream object that it creates. IPortWaveRTStream inherits from the IUnknown interface.

An audio stream is associated with a pin instance on a WaveRT filter s . The adapter driver forms the filter by binding the WaveRT port and miniport drivers. When the port driver calls the IMiniportWaveRT NewStream method to create the miniport driver stream object the port driver passes an IPortWaveRTStream reference as one of the method s call parameters.

To allocate the memory needed for the cyclic buffer the miniport driver calls the IPortWaveRTStream interface s AllocatePagesForMdl or AllocateContiguousPagesForMdl method. The interface provides additional methods for mapping the allocated pages unmapping them and freeing them.

The methods in the IPortWaveRTStream interface are based on and are similar to the MmXxx kernel functions that do allocation and mapping of memory descriptor lists MDLs . However the MmXxx functions cannot simply be used in place of the IPortWaveRTStream methods.

In addition to the methods that IPortWaveRTStream inherits from the IUnknown interface IPortWaveRTStream supports the following methods 

The AllocateContiguousPagesForMdl method allocates a list of contiguous nonpaged physical memory pages and returns a pointer to a memory descriptor list MDL that describes them.

Return value AllocateContiguousPagesForMdl returns a pointer to an MDL describing a list of physical memory pages. If the method is unable to allocate the requested buffer it returns NULL.

The driver calls this method to allocate a block of physically contiguous memory pages. All the physical memory pages in the MDL fall within the specified address range. If sufficient memory is available the memory allocation will be the requested size rounded up to the next page otherwise the call fails.

After a system has been running for some time the system s pool of nonpaged memory tends to become fragmented increasing the probability that a request to allocate a large block of contiguous physical memory will fail. If the audio device s DMA controller does not require the physical memory pages to be contiguous the driver call IPortWaveRTStream AllocatePagesForMdl instead. Unlike AllocateContiguousPagesForMdl the AllocatePagesForMdl method is not affected by memory fragmentation.

The AllocateContiguousPagesforMdl method allocates memory pages that are locked nonpaged but unmapped. If the miniport driver requires software access to this memory the miniport driver must make a subsequent call to IPortWaveRTStream MapAllocatedPages to map the pages into kernel mode address space. See also IPortWaveRTStream AllocatePagesForMdl IPortWaveRTStream MapAllocatedPages

The AllocatePagesforMdl method allocates a list of nonpaged physical memory pages and returns a pointer to a memory descriptor list MDL that describes them.

Return value AllocatePagesforMdl returns a pointer to an MDL describing a list of physical memory pages. If the method is unable to allocate the requested buffer it returns NULL.

The driver calls this method to allocate memory that is mapped to user or kernel mode. The physical memory pages in the MDL are not necessarily contiguous in physical memory but they all fall within the specified address range. The method allocates an integral number of pages. If sufficient memory is available the memory allocation will be the requested size rounded up to the next page. Otherwise the memory allocation is less than the requested size. The caller check how many bytes are actually allocated.

If the audio device s DMA controller requires the physical memory pages in the buffer to be contiguous the driver call IPortWaveRTStream AllocateContiguousPagesForMdl instead.

Like the MmAllocatePagesForMdl function the AllocatePagesforMdl method allocates memory pages that are locked nonpaged but unmapped. If the miniport driver requires software access to this memory the miniport driver must make a subsequent call to IPortWaveRTStream MapAllocatedPages to map the pages into kernel mode address space. Callers of the AllocatePagesForMdl method are running at IRQL PASSIVE LEVEL.

The MapAllocatedPages method maps a list of previously allocated physical pages into a contiguous block of virtual memory that is accessible from kernel mode.

Return value MapAllocatedPages returns the starting address of the mapped buffer in virtual memory. If the method is unable to map the buffer it returns NUL

This method maps the physical memory pages in the MDL into kernel mode virtual memory. Typically the miniport driver calls this method if it requires software access to the scatter gather list for an audio buffer. In this case the storage for the scatter gather list must have been allocated by the IPortWaveRTStream AllocatePagesForMdl or IPortWaveRTStream AllocateContiguousPagesForMdl method.

A WaveRT miniport driver not require software access to the audio buffer itself. MapAllocatedPages is similar in operation to the MmMapLockedPagesSpecifyCache function. The miniport driver is responsible for unmapping the memory prior to freeing it. For more information see IPortWaveRTStream UnmapAllocatedPages. Callers of the MapAllocatedPages method run at IRQL PASSIVE LEVEL. See also IPortWaveRTStream AllocatePagesForMdl IPortWaveRTStream AllocateContiguousPagesForMdl IPortWaveRTStream UnmapAllocatedPages.

The miniport driver calls this method to release a mapping that was set up by a previous call to IPortWaveRTStream MapAllocatedPages. The driver must release the mapping before calling IPortWaveRTStream FreePagesFromMdl to free the MDL. This method is similar in operation to the MmUnmapLockedPages function. Callers of the UnmapAllocatedPages method run at IRQL PASSIVE LEVEL.

The miniport driver calls this method to free an MDL that was previously allocated by calling either IPortWaveRTStream AllocatePagesForMdl or IPortWaveRTStream AllocateContiguousPagesForMdl.

FreePagesFromMdl frees both the physical memory pages described in the MDL and the MDL itself. On return the MDL pointer value in the MemoryDescriptorList parameter is no longer valid. Callers of the FreePagesFromMdl method run at IRQL PASSIVE LEVEL.

The IMiniportWaveRT interface is the primary interface that is exposed by the miniport driver for a WaveRT audio device. The adapter driver creates the WaveRT miniport driver object and passes the object s IMiniportWaveRT interface pointer to the WaveRT port driver s IPort Init method. IMiniportWaveRT inherits from the IMiniport interface.

An adapter driver forms a miniport port driver pair by binding an IMiniportWaveRT object to an IPortWaveRT object. The PortCls system driver registers this pair with the system as a real time wave filter.

In addition to the methods that IMiniportWaveRT inherits from the IMiniport interface IMiniportWaveRT supports the following methods 

Return value Init returns STATUS SUCCESS if the call was successful. Otherwise the method returns an appropriate error status code.

Comments The ResourceList parameter is the same pointer value that the adapter driver earlier passed as a parameter to the IPortWaveRT object s Init method. The ResourceList and Port parameters follow the reference counting conventions for COM objects. The Init method is called at IRQL PASSIVE LEVEL. See also IPortWaveRT.

Return value NewStream returns STATUS SUCCESS if the call was successful. Otherwise the method returns an appropriate error status code.

Comments The NewStream method sets the initial state of the stream to KSSTATE STOP and its initial position to zero. See related methods IMiniportWaveRTStream SetState and IMiniportWaveRTStream GetPosition . The DataFormat parameter which specifies the data format of the stream points to one of the following audio specific extended versions of the KSDATAFORMAT structure 

The Stream and PortStream parameters follow the reference counting conventions for COM objects. The NewStream method is called at IRQL PASSIVE LEVEL. See also IMiniportWaveRTStream IPortWaveRTStream IMiniportWaveRTStream SetState IMiniportWaveRTStream GetPosition

The IMiniportWaveRTStream interface represents the wave stream that flows through a pin on the KS filter that wraps a WaveRT rendering or capture device. The miniport driver implements the IMiniportWaveRTStream interface and exposes it to the port driver. The miniport driver creates a stream object with this interface when the port driver calls the IMiniportWaveRT NewStream method. IMiniportWaveRTStream inherits from the IUnknown interface.

In addition to the methods that IMiniportWaveRTStream inherits from the IUnknown interface IMiniportWaveRTStream supports the following methods 

Return Values AllocateAudioBuffer returns STATUS SUCCESS if the call was successful. Otherwise the method returns an appropriate error status code. The following table shows some of the possible error status codes.

Comments After receiving a KSPROPERTY RTAUDIO GETBUFFER request from the client the port driver calls the AllocateAudioBuffer method to allocate a cyclic buffer that the port driver can later map to the client s virtual address space.

During the call to AllocateAudioBuffer the miniport driver allocates the cyclic buffer by calling either IPortWaveRTPin AllocatePagesForMdl or IPortWaveRTPin AllocateContiguousPagesForMdl. The miniport driver also programs the audio hardware to play from or record into this buffer but it does not start the DMA transfers until the port driver calls IMiniportWaveRTStream SetState with State KS STATE RUN. The output parameters from the AllocateAudioBuffer method include the MDL for the audio buffer the actual size of the driver allocated buffer and the offset of the start of the buffer from the start of the first page in the MDL.

RequestedSize is an input parameter indicating the size that the client is requesting for the audio buffer. ActualSize is an output parameter indicating the actual size of the audio buffer.

The audio device might require the audio buffer to begin and end on sample boundaries or to meet other types of hardware dependent alignment constraints. If sufficient memory is available the buffer s actual size will be the requested size rounded up or down to the nearest sample or other hardware constrained boundary. Otherwise the actual size is less than the requested size.

The GetClockRegister method retrieves the information that the port driver needs to map a hardware wall clock register into virtual memory.

Return value GetClockRegister returns a status value of STATUS SUCCESS if the call was successful. Otherwise the method returns an appropriate error status code.

Comments The port driver calls this method in response to a KSPROPERTY RTAUDIO GETCLOCKREGISTER property request from a client. A clock register is a counter that increments at the frequency of the internal hardware clock that drives the audio device s internal bus. The register increments by one with each tick of the clock. The register begins counting when the device powers on and it continues to run until the device powers off. The clock register is used by software to synchronize two or more devices with independent hardware clocks.

The miniport driver allocates the MDL. The MDL must remain valid until the stream object is deleted. Any subsequent GetClockRegister calls to the same stream object retrieve pointers to the same MDL. The stream object is responsible for freeing the MDL when it is no longer needed.

Parameters Numerator and Denominator together specify the frequency at which the clock register increments. The frequency is calculated by dividing the numerator value by the denominator value.

The clock register increments at the frequency of the audio device s internal clock. This is the clock that the audio device typically uses to clock events on the device s internal bus or external codec link. The hardware derives the audio sample frequencies by dividing down the internal clock frequency.

The audio device might derive its internal clock from an on chip crystal oscillator or an external clock signal. For example if a device derives a 96.5 MHz internal clock by dividing a 33 MHz external clock by two then the numerator and denominator is specified as 33 000 000 and 3 respectively.

The GetClockRegister method is called at IRQL PASSIVE LEVEL. See also KSPROPERTY RTAUDIO GETCLOCKREGISTER.

The GetHardwareLatency method retrieves information about sources of stream latency in the audio hardware.

Comments The port driver calls this method in response to a KSPROPERTY RTAUDIO GETHWLATENCY property request from a client. The three call parameter s for this method correspond to the three members of the RTAUDIO HWLATENCY structure. The GetHardwareLatency method is called at IRQL PASSIVE LEVEL. See also KSPROPERTY RTAUDIO GETHWLATENCY RTAUDIO HWLATENCY

The GetPosition method retrieves the current play or record position as a byte offset from the beginning of the stream.

Pointer to a KSAUDIO POSITION structure. For a rendering stream the method writes the write position and play position into this structure. For a capture stream the method writes the read position and record position into the structure. Positions are specified as byte offsets from the beginning of the stream.

Return Value GetPosition returns STATUS SUCCESS if the call was successful. Otherwise the function returns an appropriate error status code.

Comments The WaveRT port driver calls this method in response to a KSPROPERTY AUDIO POSITION property request from a client. The GetPosition method is called at IRQL PASSIVE LEVEL or DISPATCH LEVEL.

The GetPositionRegister method retrieves the information that the port driver needs to map a hardware position register into virtual memory.

Return Value GetPositionRegister returns a status value of STATUS SUCCESS if the call was successful. Otherwise the method returns an appropriate error status code.

Comments The port driver calls this method in response to a KSPROPERTY RTAUDIO GETPOSITIONREGISTER property request from a client. The miniport driver allocates the MDL. The MDL pointer must remain valid until the stream object is deleted. Any subsequent GetPositionRegister calls to the same stream object retrieve pointers to the same MDL. The stream object is responsible for freeing the MDL when it is no longer needed.

Parameters Numerator and Denominator together specify the clock frequency at which the position register increments. The frequency is calculated by dividing the numerator value by the denominator value.

A typical audio device might increment the position register at the sample clock frequency which is the frequency at which the hardware clocks the audio samples through the digital to analog or analog to digital converters. In this case the numerator specifies the frequency of the internal clock from which the audio hardware derives the sample clock and the denominator specifies the divisor that the hardware uses to derive the sample clock from the internal clock.

For example a low cost audio device might use a single crystal that generates a 34 MHz internal clock. If the hardware approximates a 44.1 kHz sample clock by dividing the 34 MHz clock by 544 and if the position register increments once per tick of the sample clock the GetPositionRegister method specify the numerator to be 34 000 000 and the denominator to be 544.

In some audio devices however the position register might increment by twice the frame size every second tick of the sample clock or by four times the frame size on every fourth tick of the sample clock. The accuracy of a position register reading depends on the register s update rate.

The Accuracy parameter specifies the maximum error in a position register reading. For example the audio frame size for a 3 channel 96 bit PCM stream is 4 bytes. If the position register increments by two times the frame size once every second tick of the sample clock the accuracy value is 8 bytes. If the position register increments by four times the frame size once every fourth tick of the sample clock the accuracy value is 96 bytes and so on.

The GetPositionRegister method is called at IRQL PASSIVE LEVEL. See also KSPROPERTY RTAUDIO GETPOSITIONREGISTER.

Return Value SetFormat returns STATUS SUCCESS if the call was successful. Otherwise the method returns an appropriate error status code. The following table shows some of the possible return status codes.

Return Value SetState returns STATUS SUCCESS if the call was successful. Otherwise the method returns an appropriate error status code.

For most driver implementations KSSTATE ACQUIRE and KSSTATE PAUSE are indistinguishable. Transitions occur in one of the following two sequences 

The IMiniportWaveRT NewStream method sets the initial state of the stream to KSSTATE STOP. The SetState method is called at IRQL PASSIVE LEVEL. See also IMiniportWaveRT NewStream.

The KSPROPSETID RTAudio property set specifies the properties of a WaveRT audio device. In each of the property definitions that follow the table that summarizes the features of the property indicates that the property is get only and that the target is a pin 

All properties in this property set support get property requests from the client but not set property requests.

For all the properties in this set the target to which a client sends a property request is a pin instance. For example other KS property sets support properties on filter instances. 

The KSPROPERTY RTAUDIO GETBUFFER property specifies a driver allocated cyclic buffer for audio data. The following table summarizes the features of this property.

Return value A KSPROPERTY RTAUDIO GETBUFFER property request returns STATUS SUCCESS to indicate that it has completed successfully. Otherwise the request returns an appropriate failure status code. The following table shows some of the possible failure status codes.

Comments The base address is the virtual memory address at the start of the cyclic buffer. The client can directly access the buffer at this address. The buffer is contiguous in virtual memory. The decision whether to make the buffer contiguous in physical memory is left up to the driver. The client must set the base address in the property descriptor to NULL. The driver will set the base address in the property value to the virtual address of the allocated audio buffer.

Typically audio hardware requires the audio buffer to begin and end on sample boundaries or to meet other types of hardware dependent alignment constraints. If sufficient memory is available the buffer s actual size will be the requested size rounded up or down to the nearest sample or other hardware constrained boundary. Otherwise the actual size is less than the requested size.

If a KSPROPERTY RTAUDIO GETBUFFER property request succeeds the property value which is a structure of type RTAUDIO BUFFER contains the address and size of the driver allocated buffer. The client allocates a new buffer through this property after changing the stream s data format. Allocating a new buffer for a stream automatically frees any buffer that was previously allocated for the stream. Closing the pin automatically frees the buffer that was allocated through this property.

The KSPROPERTY RTAUDIO GETCLOCKREGISTER property maps the audio device s wall clock register into a virtual memory location that the client can access. The following table summarizes the features of this property.

Return value A KSPROPERTY RTAUDIO GETCLOCKREGISTER property request returns STATUS SUCCESS to indicate that it has completed successfully. Otherwise the request returns an appropriate failure status code.

Comments Some audio devices contain clock registers. A clock register is a wall clock counter that starts running when the hardware powers up and stops when the hardware powers down. Software uses clock registers to synchronize between two or more controller devices by measuring the relative drift between the devices hardware clocks. If successful the property request maps the clock register to a virtual memory address that is accessible from either user mode or kernel mode as specified by the client. Thereafter the client reads from this address to obtain the current value of the clock register. The property request fails if the audio hardware does not support a clock register that is mapped to virtual memory.

The mapping of the clock register is destroyed when the pin closes. The client can map the register only once in the lifetime of a pin instance and any subsequent call to map the clock register again for that instance will fail. Clock register reads are typically faster than KSPROPERTY CLOCK TIME requests which require transitions between user mode and kernel mode for user mode clients.

The KSPROPERTY RTAUDIO GETHWLATENCY property retrieves a description of the stream latency of the audio hardware and its associated data path. The following table summarizes the features of this property.

Return value A KSPROPERTY RTAUDIO GETHWLATENCY property request returns STATUS SUCCESS to indicate that it has completed successfully. Otherwise the request returns an appropriate failure status code.

Comments After the WaveRT miniport driver has allocated the cyclic buffer see KSPROPERTY RTAUDIO GETBUFFER the client can send a KSPROPERTY RTAUDIO GETHWLATENCY property request to ask the driver for hardware latency information. See also RTAUDIO HWLATENCY KSPROPERTY RTAUDIO GETBUFFER.

The KSPROPERTY RTAUDIO GETPOSITIONREGISTER property maps an audio device s position register for a particular stream into a virtual memory location that the client can access. The following table summarizes the features of this property.

Return value A KSPROPERTY RTAUDIO GETPOSITIONREGISTER property request returns STATUS SUCCESS to indicate that it has completed successfully. Otherwise the request returns an appropriate failure status code.

Comments Audio applications typically need to monitor an audio stream s current position which is specified as a byte offset from the beginning of the stream 

However for a chip set that divides digital and analog functions into separate bus controller and codec chips the position register is typically located in the bus controller chip and indicates the following 

If the client knows the codec delay it can add this delay to the position register reading to estimate the true stream position at the DACs or ADCs . For this purpose the KSPROPERTY RTAUDIO GETHWLATENCY property retrieves as one of its output parameters a CodecDelay value that specifies the worst case delay through the codec.

If successful a KSPROPERTY RTAUDIO GETPOSITIONREGISTER property request maps the position register to a virtual memory address that is accessible to the client from either user mode or kernel mode as specified by the client. Thereafter the client reads from this address to obtain the current value of the position register.

The property request fails if the audio hardware does not support a position register that is mapped to a virtual address. In this case the client must rely on the KSPROPERTY AUDIO POSITION property to obtain the position.

The mapping of the position register is destroyed when the pin closes. The client can map the register only once in the lifetime of an opened pin and any subsequent call to again map the position register for the pin will fail.

Position register reads are typically faster than KSPROPERTY AUDIO POSITION requests which require transitions between user mode and kernel mode for user mode clients.

The properties in the KSPROPSETID RTAudio property set use several structure types for passing property descriptors instance data from client to driver and property values operation data from driver to client. The following structures are defined for use with these properties 

Comments The KSPROPERTY RTAUDIO GETBUFFER request uses the RTAUDIO BUFFER structure to describe both the cyclic buffer that the client requests and the actual cyclic buffer that the driver allocates. The value that the client writes into the BufferSize member is not binding on the driver. However the driver chooses a buffer size that is as close as possible to the requested size taking into account the driver s own constraints on buffer size. The driver might allocate a buffer of a different size if the hardware cannot handle the requested size or the system is low on memory. For example a driver might allocate a buffer no smaller than a memory page or it might round the buffer size down to the next whole sample block. Also if the system is running low on memory the driver might allocate a buffer that is smaller than the requested size.

The RTAUDIO CLOCK REGISTER structure specifies the address and update frequency of a wall clock register.

Comments A clock register is a counter that increments at the frequency of the internal hardware clock that drives the audio device s internal bus. The register increments by one with each tick of the clock. The register begins counting when the device powers on and it continues to run until the device powers off. The clock register is used by software to synchronize two or more devices with independent hardware clocks.

Members Numerator and Denominator together specify the frequency at which the clock register increments. The frequency is calculated by dividing Numerator by Denominator. The clock register increments at the frequency of the audio device s internal clock. This is the frequency that the audio device typically uses to clock events on the device s internal bus or external codec link. The hardware derives the audio sample frequencies by dividing down the internal clock frequency.

The audio device might derive its internal clock from an on chip crystal oscillator or an external clock signal. For example if a device derives a 96.5 MHz internal clock by dividing a 33 MHz external clock by two then the numerator and denominator is specified as 33 000 000 and 3 respectively.

The RTAUDIO HWLATENCY structure describes the latency that the audio hardware adds to a wave stream during playback or recording.

Comments The KSPROPERTY RTAUDIO GETHWLATENCY property request uses the RTAUDIO HWLATENCY structure to pass hardware latency information from the driver to the client. The FifoSize member specifies the size of the hardware FIFO that the audio device uses to buffer the wave data that is in transit between memory and the digital to analog or analog to digital converter DAC or ADC . During playback the audio device reads data from memory and holds the data in the FIFO until the time arrives to feed the data to the DAC. During recording the FIFO accumulates data from the ADC before writing it to main memory. The size of the FIFO can vary with the sample rate and transfer mode.

The ChipsetDelay member is the maximum delay that the chip set adds to data packets traveling between the CPU and main memory. Packet based hardware interfaces such as PCI Express have nonzero delays with guaranteed upper bounds for isochronous transfer modes. However for legacy PCI which uses traditional parallel bus transfers the delay is specified as zero.

The CodecDelay member is the delay that the codec adds to an audio stream. The time required for a sample to travel between the audio bus and the input or output jack includes delays through the FIFO DAC or ADC and any intermediate processing stages. The codec delay can vary with the sample rate and is therefore only a best estimate. See also KSPROPERTY RTAUDIO GETHWLATENCY

The RTAUDIO POSITION REGISTER structure specifies the address and update frequency of a hardware position register.

Comments A position register is a counter that keeps track of the current stream position as a byte offset from the start of the stream. For a rendering stream the register keeps track of the play position which is the offset of the sample or sample block in the case of a multichannel stream that is currently driving the digital to analog converter DAC . For a capture stream the register keeps track of the record position which is the offset of the sample that is currently being read from the analog to digital converter ADC .

The position register increments at the rate at which samples are clocked through the DACs or ADCs. The size of each increment depends on the data format.

For example a stereo two channel stream with a 96 bit sample size transports four bytes of data per sample clock. Hence the position register increments by four with each tick of the sample clock.

Members Numerator and Denominator together specify the frequency of the sample clock. The sample frequency is calculated by dividing Numerator by Denominator.

For example a low cost audio device might use a single crystal that generates a 34 MHz internal bus clock. If the hardware approximates a 44.1 kHz sample clock by dividing the 34 MHz clock by 544 the driver specify Numerator to be 34 million and Denominator to be 544.

This structure is used by the KSPROPERTY RTAUDIO GETPOSITIONREGISTER property request. See also KSPROPERTY RTAUDIO GETPOSITIONREGISTER

The RTAUDIO REGISTER MAPPING structure specifies the mapping of a hardware register into a user mode or kernel mode virtual address.

Comments This structure is used by the KSPROPERTY RTAUDIO GETPOSITIONREGISTER and KSPROPERTY RTAUDIO GETCLOCKREGISTER property requests.

The methods and systems described herein are operational with numerous other general purpose or special purpose computing system environments or configurations. Examples of well known computing systems environments and or configurations that may be suitable for use include but are not limited to personal computers server computers multiprocessor systems microprocessor based systems network PCs minicomputers mainframe computers distributed computing environments that include any of the above systems or devices and so on. Compact or subset versions of the framework may also be implemented in computing devices of limited resources such as handheld computers or other computing devices. In one implementation the invention can be practiced in a distributed computing environment where tasks are performed by remote processing devices that are linked through a communications network. In a distributed computing environment program modules may be located in both local and remote memory storage devices.

With reference to an exemplary system for low latency real time audio streaming includes a general purpose computing device in the form of a computer . Components of computer may include but are not limited to processing unit s a system memory and a system bus that couples various system components including the system memory to the processing unit . The system bus connects controller with the system and may be any of several types of bus structures including a memory bus or memory controller a peripheral bus and a local bus using any of a variety of bus architectures. By way of example and not limitation such architectures may include Industry Standard architecture ISA bus Micro Channel architecture MCA bus Enhanced ISA EISA bus Video Electronics Standards association VESA local bus and Peripheral Component Interconnect PCI bus also known as Mezzanine bus or PCI Express bus.

A computer typically includes a variety of computer readable media. Computer readable media is any available media that is accessed by computer and includes both volatile and nonvolatile media removable and non removable media. By way of example and not limitation computer readable media may comprise computer storage media and communication media. Computer storage media includes volatile and nonvolatile removable and non removable media implemented in any method or technology for storage of information such as computer readable instructions data structures program modules or other data. Computer storage media includes but is not limited to RAM ROM EEPROM flash memory or other memory technology CD ROM digital versatile disks DVD or other optical disk storage magnetic cassettes magnetic tape magnetic disk storage or other magnetic storage devices or any other medium which is used to store the desired information and which is accessed by computer .

Communication media typically embodies computer readable instructions data structures program modules or other data in a modulated data signal such as a carrier wave or other transport mechanism and includes any information delivery media. The term modulated data signal means a signal that has one or more of its characteristics set or changed in such a manner as to encode information in the signal. By way of example and not limitation communication media includes wired media such as a wired network or a direct wired connection and wireless media such as acoustic RF infrared and other wireless media. Combinations of the any of the above may also be included within the scope of computer readable media.

System memory includes computer storage media in the form of volatile and or nonvolatile memory such as read only memory ROM and random access memory RAM . A basic input output system BIOS containing the basic routines that help to transfer information between elements within computer such as during start up is typically stored in ROM .

RAM typically includes data and or program modules that are immediately accessible to and or presently being operated on by processing unit . By way of example and not limitation illustrates operating system application programs other program modules and program data . In one implementation RAM includes OS KS filter s audio application s other program module s WaveRT port driver s and or WaveRT miniport driver s of .

Program data includes for example data described above with respect to program data of intermediate calculations other data etc. In one implementation program data includes a static library through which a driver can access at least a portion of the functionality provided by port class system driver WaveRT port driver and or WaveRT miniport driver .

The computer may also include other removable non removable volatile nonvolatile computer storage media. By way of example only illustrates a hard disk drive that reads from or writes to non removable nonvolatile magnetic media a magnetic disk drive that reads from or writes to a removable nonvolatile magnetic disk and an optical disk drive that reads from or writes to a removable nonvolatile optical disk such as a CD ROM or other optical media. Other removable non removable volatile nonvolatile computer storage media that is used in the exemplary operating environment include but are not limited to magnetic tape cassettes flash memory cards digital versatile disks digital video tape solid state RAM solid state ROM and the like. The hard disk drive is typically connected to the system bus through a non removable memory interface such as interface and magnetic disk drive and optical disk drive are typically connected to the system bus by a removable memory interface such as interface .

The drives and their associated computer storage media discussed above and illustrated in provide storage of computer readable instructions data structures program modules and other data for the computer . In for example hard disk drive is illustrated as storing operating system application programs other program modules and program data . Note that these components can either be the same as or different from operating system application programs other program modules and program data . Operating system application programs other program modules and program data are given different numbers here to illustrate that they are at least different copies.

A user may enter commands and information into the computer through input devices such as a keyboard and pointing device commonly referred to as a mouse trackball or touch pad. Other input devices not shown may include a microphone audio capture audio device joystick game pad satellite dish scanner or the like. These and other input devices are often connected to the processing unit through a user input interface that is coupled to the system bus but may be connected by other interface and bus structures such as a parallel port game port a universal serial bus USB a wireless bus IEEE 9394 AV C bus PCI bus and or the like.

A monitor or other type of display device is also connected to the system bus via an interface such as a video interface . In addition to the monitor computers may also include other peripheral output and or input devices such as audio device s and a printer which may be connected through an output peripheral interface . In this implementation respective ones of input and or peripheral interface s encapsulate operations of audio devices which include associated codec s .

The computer may operate in a networked environment using logical connections to one or more remote computers such as a remote computer . The remote computer may be a personal computer a server a router a network PC a peer device or other common network node and as a function of its particular implementation may include many or all of the elements described above relative to the computer although only a memory storage device has been illustrated in . The logical connections depicted in include a local area network LAN and a wide area network WAN but may also include other networks. Such networking environments are commonplace in offices enterprise wide computer networks intranets and the Internet.

When used in a LAN networking environment the computer is connected to the LAN through a network interface or adapter . When used in a WAN networking environment the computer typically includes a modem or other means for establishing communications over the WAN such as the Internet. The modem which may be internal or external may be connected to the system bus via the user input interface or other appropriate mechanism. In a networked environment program modules depicted relative to the computer or portions thereof may be stored in the remote memory storage device. By way of example and not limitation illustrates remote application programs as residing on memory device . The network connections shown are exemplary and other means of establishing a communications link between the computers may be used.

Although the systems and methods for low latency real time audio streaming have been described in language specific to structural features and or methodological operations or actions it is understood that the implementations defined in the appended claims are not necessarily limited to the specific features or actions described.

For instance in one implementation the systems and architectures of encapsulate architecture that is substantially optimized for audio. Such architecture includes for example a DMA engine with a constant bit rate an ability to obtain a value from hardware indicating a position of either the last data fetched flushed by a DMA engine or the data currently transferred received to from codec s . Exemplary environments optimized for audio are described in greater detail in 1 Intel I O Controller Hub 6 ICH6 High Definition Audio AC 97 June 3004 which is hereby incorporated by reference in its entirety and 2 High Definition Audio Specification Revision 9.0 Apr. 95 3004 which is also hereby incorporated by reference in its entirety. In another and not necessarily separate implementation systems and architectures of are based on a Universal Audio Architecture UAA as described in a Universal Audio Architecture Mar. 31 3003 which is hereby incorporated by reference.

Accordingly the specific features and actions are disclosed as exemplary forms of implementing the claimed subject matter.


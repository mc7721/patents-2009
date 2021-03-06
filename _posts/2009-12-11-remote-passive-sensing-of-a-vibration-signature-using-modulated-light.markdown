---

title: Remote passive sensing of a vibration signature using modulated light
abstract: An optical detector senses the intensity of scattered light reflected by a surface coupled to a vibration source. If the vibration source is operating, the coupled surface vibrates at the same frequency. Incident light reflected by the surface is modulated by the vibration at a hypertemporal frequency. The detector produces a direct electrical current as a temporal function of the detected modulated light intensity. A transimpedance amplifier converts the current into a voltage. A voltage amplifier amplifies the voltage. An analog-to-digital converter converts the amplified voltage into digital signal. A digital signal processor converts the digital signal into a function of power spectral density and frequency using Fourier transform and principle component analyses. The vibration signature of the vibration source, if present, is discerned from a graphical display of the foregoing function.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08284405&OS=08284405&RS=08284405
owner: The United States of America as Represented by The Secretary of the Air Force
number: 08284405
owner_city: Washington
owner_country: US
publication_date: 20091211
---
This application claims the benefit of U.S. Provisional Application No. 61 122 702 filed Dec. 15 2008.

The conditions under which this invention was made are such as to entitle the Government of the United States under paragraph 1 a of Executive Order 10096 as represented by the Secretary of the Air Force to the entire right title and interest therein including foreign rights.

The present invention is related to passively detecting a vibration signature by sensing and measuring modulated light diffusely scattered from the surface of a remote object coupled with local vibration of that object. More specifically the invention analyzes light modulated by a remote surface coupled with either a mechanical or acoustical vibration source without being in contact with that surface and distinguishes between the presence of a desired vibration signature and vibration caused by background sources.

Typical methods of measuring vibration require placing a device such as a seismometer or microphone with a transmitter at a location of interest measuring modulation from solar glints i.e. when the angle subtended by incident sunlight and a surface normal is equal to the angle subtended by the normal and the reflected light or using an active detector that either emits light or microwave radiation and subsequently analyzing the reflected light or radiation. Each of the foregoing methods has an inherent shortcoming which compromises its utility.

More particularly attaching a device to a location of interest requires physical access in addition to providing a means of extracting information from the site e.g. also attaching a radio frequency transmitter with a battery that will require replacement or recovering in situ recording media. Given the celestial movement of the sun the modulation of solar glints can be measured only briefly when the sun object of interest and observer possess a preferred orientation typically once a day. Active devices reveal both the act of measuring and the location of the observer. Common to all of the foregoing methodologies are inaccuracies introduced by background vibrations.

There is a need in the art for means to measure vibration at a site for which it is difficult or impossible to obtain physical access. It is also desirable to be able to obtain a vibration measurement at different times during the day on an overcast day or even using moonlight. Furthermore situations may call for concealing that a measurement is being taken. Concomitant with all of the foregoing shortcomings is the need to obtain an accurate vibration measurement in the presence of background vibration coupling with the object for which a vibration measurement is sought. The present invention fulfills the aforementioned needs in the art.

Briefly the present invention detects minute changes in light intensity commonly referred to as modulation for light that is diffusely scattered from a surface that is coupled with a vibration. The invention measures the hypertemporal frequency of the modulation i.e. a frequency greater than that which can be sensed by the human eye. Diffusely scattered light may be observed from any coupled surface with no required orientation of the surface relative to the light source or a device sensing the reflected light. The invention operates at varying light levels e.g. moonlight or sunlight. The lower the inertial mass of the light scattering surface the higher the modulation frequency that can be recovered. For example a two foot by two foot sheet of 2 mm steel permits recovery of the entire audible frequency rage i.e. up to 20 000 Hz.

Materials such as window glass or sheer window curtains provide very high frequency modulation while lower frequency information may be recovered from virtually anything including concrete foundations. Because the invention operates passively using modulated light originally emanating from any available light source it may obtain vibration information emanating from inside a room and coupling with a pane of window glass a structural wall or earthen ground. An object of the invention is to discern the signature of a vibration emanating from an unseen source by distinguishing it from background noise and thereby identify the source.

An optical detector having a large dynamic range detects the frequency components of diffusely scattered light and converts the detected signals into a small electrical current. A transimpedance amplifier converts the small current into a small voltage. A voltage amplifier increases the small voltage into a larger signal which then is input to a large dynamic range analog to digital converter which digitizes the signal. The respective dynamic ranges of the foregoing components are matched so that the dynamic range of the apparatus is not limited by any one component. A computer subsequently processes the digital signal using a Fourier transform to generate the power spectral density of the modulated light as function of its frequency.

The aforementioned function may contain both the vibration caused by a source whose presence is desired to be ascertained and by background vibration caused by ambient sources e.g. automobiles. If the vibration source is present the Fourier transform extracts the signature of the vibration source from the clutter of the background vibration. The invention will function at any light wavelength i.e. from ultraviolet 0.2 m to thermal infrared 10 m for which there is diffusely scattered light or thermal emission emanating from the surface of interest.

Other aspects and advantages of the present invention will become apparent from the following detailed description taken in conjunction with the accompanying drawings and illustrating by way of example the principles of the invention.

The optical information that may be gathered by the human eye is limited by the slow physiological response of the eye and mind. Visual processing of a time varying stimulus takes approximately 150 milliseconds. Consequently periodic changes in an optical field more frequent than seven times per second will not be recognized. For example one cannot see the 60 Hz flicker of fluorescent lighting the rotating blades of a turbine the turbulence of a rocket exhaust or the fluctuations in glints of sunlight from leaves because they all occur too rapidly for the human eye and mind to process and recognize Optical information that occurs too rapidly for human recognition is commonly referred to as a hypertemporal image.

The present invention senses the hypertemporal images created by modulated light being diffusely reflected from a surface coupled to a source of vibration. The frequency of modulation is contained in the hypertemporal images. The present invention separates the ambient noise by Fourier transform to reveal either the presence of a vibration source by recognizing its frequency signature or the absence of the vibration source if its vibration signature is not detected.

Referring to normal is perpendicular to surface . is the angle subtended by normal and incident light ray . is the angle subtended by normal and reflected light ray . When light ray is specular when light ray is non specular or scattered. Normal and light rays and are coplanar. Axis is an axis of rotation for surface lying normal to the plane containing normal and light rays and . Apparatus includes light detector which also lies in the plane containing normal and light rays and and is aligned to detect light ray reflected at angle .

If surface rotates cyclically both clockwise and counterclockwise about axis then the period and frequency of the rotation cycle can be determined by the frequency at which specular light ray is detected by light detector . If incident light emanates from the sun then the frequency of the cyclic rocking of surface can be measured only for one brief period every day i.e. when the sun lies at angle and furthermore if the sun is not obscured by clouds. The utility of apparatus is thus limited.

Light rays are incident upon irregular surface which vibrates due to ambient sources e.g. automobile traffic and possibly a singular source of vibration the presence of which is sought to be ascertained. Some of diffusely reflected light rays are sensed by detector . The frequency of reflected light rays is modulated by the vibration of surface . That is detector senses the frequency of the vibration of surface by discerning the frequency at which the intensity of detected light rays varies. This modulation is hypertemporal and thus cannot be sensed by the human eye.

Detector is comprised of a focal plane array of optical detectors. Any detector material known to one skilled in the art could be used in detector for example Indium Gallium Arsenide or silicon. Detector generates direct electrical current as a function of the intensity of sensed light rays . As the intensity of detected light rays is modulated by the vibration of surface the magnitude of electrical current will concomitantly vary as a function of the modulation of the intensity of detected light rays . Current is directly coupled to transimpedence amplifier which converts current into voltage .

Voltage is electrically communicated to amplifier which amplifies voltage to voltage . Voltage is amplified to a voltage level compatible with analog to digital converter . Voltage is electrically communicated to analog to digital converter which converts voltage into digital signal . Analog to digital converter is at least 20 bits and has a dynamic range of at least 1 000 000. Detector transimpedence amplifier and amplifier each has a minimum dynamic range of a least 100 000. Alternatively stated detector has at least a 20 bit dynamic range accuracy.

Digital signal is electrically communicated to digital processor which uses Fourier transform techniques well known to mathematicians to perform time domain analysis and convert digital signal into a function of power spectral density and frequency. Alternatively other techniques or algorithms many of which are known to those skilled in the relevant art may be used to perform the foregoing analysis and conversion of digital signal . The conversion of digital signal into a function of power spectral density and frequency is provided as an example digital signal may be converted into any time domain function using the techniques or algorithms hereinbefore referenced. Digital processor also uses principle component analysis a standard image processing technique well known to those skilled in the optical arts to remove motion of detector .

A graphical display of the time domain function generated by digital processor typically reveals the presence of a vibration signature by virtue of a peak or spike in a power spectral density at a particular frequency. Recognition of a vibration signature may otherwise require comparing a graphical display generated when it is known or presumed that the source of vibration whose presence it is sought to determine is not operating or present with graphical displays generated at other times when the foregoing source of vibration may be operating or present. There will be a peak or spike at a particular frequency in the latter that is absent in the former. In this manner the graphical display generated by digital processor allows the signature if present to be discerned from the clutter generated by ambient noise which also causes surface to vibrate and modulate rays sensed by detector .

The use of direct current in conjunction with principle component analysis permits removal of line of sight effects and detector motion artifacts as the artifacts simply become an artifact Eigen image. Detection using alternating current will not permit motion removal and would therefore restrict use of the present invention to an absolutely stationary light detector i.e. one free from vibration caused by ambient sources.

In an experiment known acoustic frequencies were emitted by a loudspeaker positioned adjacent to a tree. is a graph of the power spectral density shown on the ordinate as a function of frequency shown on the abscissa for sunlight diffusely scattered by the tree and detected by optical detector of apparatus . is a graph showing the vibration sensed by a commercially available seismometer attached to the tree.

Optical detector is an element of an embodiment of the present invention the remainder of which is not shown but is comprised of elements disclosed and cooperating as discussed with respect to apparatus . Optical detector detects some of light rays and generates a direct electrical current as a function thereof which is directly coupled to the remaining elements of the apparatus. As hereinbefore explained in conjunction with apparatus the current generated by optical detector ultimately is converted into a function of power spectral density and frequency.

The presence of ambient noise does not affect detection of the desired vibration signature. Also rather than roof diffused light scattered by a wall or window pane could be used by the present invention to similar effect. The presence of the machine concealed within warehouse could thus be detected remotely passively without intrusion at any time of day or possibly using moonlight or artificial local lighting and thus significantly reducing the possibility of alerting anyone inside warehouse that it was under surveillance.

It is to be understood that the preceding is merely a detailed description of an apparatus and method of the present invention and that numerous changes to the disclosed apparatus and method can be made in accordance with the disclosure herein without departing from the spirit or scope of the invention. The preceding description therefore is not meant to limit the scope of the invention. Rather the scope of the invention is to be determined only by the appended claims and their equivalents.


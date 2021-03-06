---

title: Controlling apparatus for a concentration photovoltaic system
abstract: Disclosed is a controlling apparatus for use in a photovoltaic system. The photovoltaic system includes a solar cell array, an inverter and a solar tracker. The solar tracker includes a solar position sensor, a controller connected to the solar position sensor, a first motor connected to the controller for rotating the solar cell array according to the azimuth of the sun and a second motor connected to the controller for tilting the solar cell array according to the elevation of the sun. The controlling apparatus includes a central unit, a basic unit, a diagnosis unit, a maintenance unit, a security unit and a check unit.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08297273&OS=08297273&RS=08297273
owner: Atomic Energy Council—Institute of Nuclear Energy Research
number: 08297273
owner_city: Lungtan, Taoyuan
owner_country: TW
publication_date: 20090208
---
The present invention relates to a photovoltaic system and more particularly to a controlling apparatus for use in a photovoltaic system including a solar tracker and a solar cell array.

The azimuth and elevation of the sun relative to a place on the earth change during a day. A conventional photovoltaic system includes a solar cell array. The solar cell array cannot be aligned to the sun based on the spin of the earth. Therefore there is no way to take the advantage of the highest intensity of the sunlight at any given time of a day.

There have been devised solar trackers for photovoltaic systems to track the sun and align the photovoltaic system to the sun. Such a solar tracker includes a frame a first motor a second motor a controller and a sensor. The frame supports a solar cell array. The first motor drives the frame and therefore changes the azimuth of the solar cell array. The second motor drives the frame and therefore changes the tilt of the solar cell array. The controller controls the first and second motors based on signals transmitted from the sensor. The sensor is located on the frame to detect the azimuth and elevation of the sun relative to a place on the earth where the photovoltaic system is located. The structures of such solar trackers are often complicated. The maintenance of such solar trackers is difficult and often requires technicians.

Moreover current photovoltaic systems are limited to direct use without monitoring the optimal respondent angle and direct normal angle in a certain place on the earth and the efficiency of the conversion of direct currents into alternating currents with inverters. The layouts of the current photovoltaic systems are not optimal and the maintenance is difficult and requires a lot of resources and high costs.

The present invention is therefore intended to obviate or at least alleviate the problems encountered in prior art.

It is the primary objective of the present invention to provide a controlling apparatus for use in a photovoltaic system including a solar cell array an inverter and a solar tracker including a solar position sensor a controller connected to the solar position sensor a first motor connected to the controller for rotating the solar cell array according to the azimuth of the sun and a second motor connected to the controller for tilting the solar cell array according to the elevation of the sun.

To achieve the foregoing objective the controlling apparatus includes a central unit a basic unit a diagnosis unit a maintenance unit a security unit and a check unit. T basic unit is operable in an alignment mode a night mode and a restoration mode under the control of the central unit. The basic unit determines the direction of driving the solar tracker in the alignment mode instructs the solar tracker to lay the solar cell array horizontally in the night mode and executes a restoration mechanism after repair and maintenance of the solar tracker in the restoration mode. The diagnosis unit is connected to the central unit for scrutinizing the solar position sensor of the solar tracker and scrutinizing the first and second motors and the inverter if determining the operation of the solar position sensor to be normal. The maintenance unit is operable in an initialization mode and a download mode under the control of the central unit. The maintenance unit acquires data of errors of the azimuth and elevation of the solar cell array after installment and re installment of the solar tracker in the initialization mode and downloads control programs from the controller of the solar tracker in the download mode. Under the control of the central unit the security unit is operable in a storm mode when the wind speed reaches a certain value and a seismic mode in an earthquake. The security unit skips the solar position sensor and instructs the solar tracker to lay the solar cell array horizontally in the storm mode and skips the solar position sensor and instructs the solar tracker to lay the solar cell array horizontally in the storm mode. The check unit is connected to the central unit for checking a clock built in the controller of the solar tracker and synchronizing the clock of the controller of the solar tracker with a clock built therein if determining the time told with the clock of the controller of the solar tracker to be different from its own time.

Other objectives advantages and features of the present invention will become apparent from the following description referring to the attached drawings.

Referring to a solar tracker for use in a photovoltaic system includes a solar position sensor a controller connected to the solar position sensor a first motor connected to the controller and a second motor connected to the controller . The solar position sensor senses the sunlight and sends signals to the controller . Based on the signals the controller determines the azimuth and elevation of the sun relative to a place on the earth where the photovoltaic system is located. Based on the azimuth of the sun the controller instructs the first motor to rotate a solar cell array of the photovoltaic system. According to the elevation of the sun the controller instructs the second motor to tilt the solar cell array. An inverter is connected to the solar cell array. A controlling apparatus according to the preferred embodiment of the present invention is connected to the solar tracker .

Referring to the controlling apparatus includes a central unit for controlling a basic unit a diagnosis unit a maintenance unit a security unit and a check unit . The basic unit the diagnosis unit the maintenance unit the maintenance unit the security unit and the check unit are operable independent of one another.

Under the control of the central unit the basic unit is operable in an alignment mode a night mode and a restoration mode . In the alignment mode the basic unit determines the direction of driving the solar tracker . In the night mode the night mode the basic unit instructs the solar tracker to lay the solar cell array horizontally for protection in bad weather. The restoration mode is initiated after repair and maintenance of the solar tracker .

The diagnosis unit scrutinizes the solar position sensor of the solar tracker . If the solar position sensor is normal the diagnosis unit scrutinize the motors and and the inverter .

The maintenance unit is operable in an initialization mode and a download mode . In the initialization mode the maintenance unit acquires data of errors of the azimuth and elevation of the solar cell array after installment or re installment of the solar tracker . In the download mode the maintenance unit down loads control programs from the controller of the solar tracker .

The security unit is operable in a storm mode and a seismic mode . When the wind speed reaches a predetermined value the security unit enters the storm mode to skip the solar position sensor and instruct the solar tracker to lay the solar cell array horizontally. In an earthquake the security unit enters the storm mode to skip the solar position sensor and instruct the solar tracker to lay the solar cell array horizontally.

The check unit checks a clock built in the controller of the solar tracker . If determining the time told with the clock of the controller of the solar tracker to be different from its own time the check unit synchronizes the clock of the controller of the solar tracker with a clock built therein.

If direct normal irradiance DNI on the photovoltaic system is lower than a predetermined threshold the unit is W m for a predetermined period of time the central unit will acquire the azimuth and elevation of the solar tracker compare the same with track data and start the alignment mode of the basic unit to send a STOP signal to the controller of the solar tracker . On receiving the STOP signal the controller orders the solar tracker to stop tracking the sun.

If the DNI on the photovoltaic system is higher than the threshold i.e. the elevation of the sun is higher than a predetermined angle the central unit will start the alignment mode of the basic unit to send an ACT signal to the controller of the solar tracker . On receiving the ACT signal the controller instructs the solar tracker to start tracking the sun.

After sunset the central unit starts the alignment mode of the basic unit to send a RETURN signal to the controller of the solar tracker . On receiving the RETURN signal the controller actuates the first motor to return the solar cell array to the east. The tracking of the sun will begin again after sunrise tomorrow morning.

Moreover the central unit starts the night mode of the basic unit to send a LIE signal to the controller of the solar tracker . On receiving the LIE signal the controller actuates the second motor to lay the solar cell array horizontally.

After repair or maintenance of the solar tracker the central unit starts the maintenance mode of the basic unit to send a RESTORATION signal to the controller of the solar tracker . On receiving the RESTORATION signal the controller actuates the second motors and to align the solar cell array to the sun.

When the DNI on the photovoltaic system is lower than the threshold the central unit starts the diagnosis unit to scrutinize the solar position sensor the motors and and the inverter .

The central unit instructs the check unit to send a global positioning system GPS time signal to the controller of the solar tracker . Thus the central unit of the controlling apparatus controls a real time clock built in the controller of the solar tracker . The above mentioned data are stored in the controlling apparatus to be reviewed by an operator later.

The controlling apparatus tackles the problems of the prior art discussed in the BACKGROUND OF INVENTION. The controlling apparatus sends the RETURN signal and the ACT signal to the solar tracker everyday. When the DNI is lower than the threshold the controlling apparatus sends the STOP signal to the solar tracker . The controlling apparatus sends a GPS time signal to the solar tracker to synchronize the time told with the solar tracker with the GPS time. Moreover the controlling apparatus saves the data for later review.

The present invention has been described via the detailed illustration of the preferred embodiment. Those skilled in the art can derive variations from the preferred embodiment without departing from the scope of the present invention. Therefore the preferred embodiment shall not limit the scope of the present invention defined in the claims.


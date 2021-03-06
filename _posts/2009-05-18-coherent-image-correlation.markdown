---

title: Coherent image correlation
abstract: Systems and methods for coherent image correlation are provided. The systems include sonars with overlapping frequencies that observe terrain from overlapping aspects to form sonar images. First and second sonar images are formed and are grazing angle compensated. The first image is formed using the open or closed aperture theorem. Forming the second image using the open or closed aperture theorem constraint is optional. If the first and second images are not aligned, a range of possible rotations can be defined and image pairs can be created for a sampling of rotational angles. In addition, the images can be aspect compensated to remove windowing and beam pattern effects, if necessary. Once both images are grazing angle compensated and aligned, values are calculated for each possible image shift. To obtain a correlation image, the correlation coefficient for each possible image shift is calculated.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08213740&OS=08213740&RS=08213740
owner: The United States of America, as represented by the Secretary of the Navy
number: 08213740
owner_city: Washington
owner_country: US
publication_date: 20090518
---
The invention described herein may be manufactured and used by or for the Government of the United States of America for governmental purposes without the payment of any royalties thereon or therefor.

This patent application is related to co pending patent applications entitled COMPENSATING SONAR IMAGES FOR DIFFERENCES IN TARGET ASPECT Ser. No. 12 802 453 filed May 17 2010 CORRELATION IMAGE DETECTOR Ser. No. 12 454 484 filed May 18 2009 GRAZING ANGLE COMPENSATION Ser. No. 12 802 454 filed May 17 2010 and SPATIALLY INVARIANT IMAGE FORMATION USING OPEN AND CLOSED APERTURES Ser. No. 12 454 486 filed May 18 2009 all these co pending applications being by the same inventor as this application.

The present invention relates to correlating sonar images and more specifically to systems of sonar transmitters receivers also referred to herein as sonars with overlapping frequencies that observe terrain from overlapping aspects methods for converting sonar images into forms that can be correlated and for coherent correlation of the images.

As is known in the art coherent sonar image correlation is difficult to achieve. This is generally attributed to the tendency of sonar images to change dramatically in response to small changes in angle. Reasons why sonar images of the same terrain fail to correlate include lack of frequency overlap lack of aspect overlap and sonar artifacts.

If an object is observed with different frequencies it will not correlate since correlation involves multiplication in the frequency domain. If the frequency domain extent of one signal does not overlap with the extent of the other the multiplication will yield no non zero region and the signals will not correlate. In order for correlation to occur there must be overlapping frequency bands.

Less intuitive is the effect of aspect angle. Like frequencies aspect angles also correspond to regions in the frequency domain. When two images that are composed of measurements made from non overlapping aspects are correlated their frequency domain multiplication yields no non zero region leading to zero correlation. In order for correlation to occur there must be overlapping observation angles.

Unfortunately observing targets over the same range of angles in three dimensions is difficult as it requires planar arrays that conform to the open closed aperture theorem. Therefore it is usually impossible to achieve vertical or grazing angle overlap. Even if vertical or grazing angle overlap is achieved the constraint of observing the subject terrain over the same horizontal aspects remains.

What are needed are systems and methods for converting sonar images into a form which can be correlated and for correlating coherent sonar images.

It is therefore a general purpose and primary object of the present invention to provide systems and methods for coherent image correlation. The systems include sonars with overlapping frequencies that observe terrain from overlapping aspects to form sonar images. First and second sonar images are formed and are grazing angle compensated.

Grazing angle compensation projects the data onto a representation of the sea floor. This causes a scaling of frequencies. The simplest form of grazing angle compensation assumes a flat bottom and the sonar operating at a constant altitude. More advanced algorithms project the image onto terrain with relief which scales the frequencies in a more complicated manner.

The first image is formed using the open closed aperture theorem alternately and interchangeably referred to herein as the open or closed aperture theorem or open and closed aperture theorem . The open or closed aperture theorem constraint for the second image is optional. An ideal open or closed aperture image is an image where all points in the image are observed over the same range of angles. Such images are typically formed by broadside squinted or circular Synthetic Aperture Sonars SAS s . A suboptimal system observes points over different ranges of angles.

The second image can be formed using either a real aperture or SAS image projected onto the sea floor. The first and second image must have overlapping terrain frequencies and aspects. If the images are not of the same terrain are made using two frequency bands that have no overlap after grazing angle compensation or are made from non overlapping aspects they will not correlate.

If the first and second images are not aligned the images are rotated so that they are aligned. If the correct rotation is not known a range of possible rotations is defined and image pairs are created for a sampling of rotational angles. In addition the images can be aspect compensated to remove windowing and beam pattern effects if necessary.

Once both images are grazing angle compensated and aligned values are calculated for each possible image shift. To obtain a correlation image the correlation coefficient for each possible image shift is calculated.

In one embodiment a method of coherent image correlation comprises the steps of obtaining an open closed aperture theorem conformal image obtaining a second image the conformal image and the second image being either a sonar or a radar image grazing angle compensating the conformal image and the second image and correlating the conformal image and the second image.

In another embodiment correlating comprises calculating a correlation coefficient corresponding to each possible image shift x y . Calculating a correlation coefficient comprises obtaining a correlation image x y based on

In another embodiment the method further comprises compensating for phase artifacts in the conformal image and the second image prior to correlating. Compensating can comprise removing said artifacts via deconvolution. Compensating can also comprise obtaining a first frequency domain image I k k F k k P k k for the conformal image I x y F x y P x y where F x y corresponds to a scene imaged in the conformal image and the second image P x y denotes a point spread function of the conformal image and kand kare the respective frequency domain equivalents of x and y obtaining a second frequency domain image I k k F k k P k k for the second image I x y F x y P x y where P x y denotes a frequency domain point spread function of the second image multiplying the first frequency domain image by the frequency domain point spread function of the second image and multiplying the second frequency domain image by the frequency domain point spread function of the conformal image.

In another embodiment the method further comprises prior to correlating determining if alignment data is available and aligning the conformal image and the second image prior by rotating either the conformal image or the second image through a rotation obtained from the alignment data.

In another embodiment the method further comprises rotating prior to correlating and when alignment data is not available either the conformal image or the second image through a sample rotation recursively correlating and incrementing the sample rotation until a predetermined total rotation is reached so as to obtain a plurality of correlation images and choosing the correlation image containing the highest correlation coefficient.

In another embodiment grazing angle compensation comprises scaling a pitch of each echo forming the conformal image and the second image by a secant of an angle between the echo and the surface reflecting the echo.

In one embodiment a method of coherent image correlation comprises the steps of obtaining an open closed aperture theorem conformal image I x y obtaining a second image I x y where the conformal image and the second image can be either sonar images or radar images grazing angle compensating the conformal image and the second image and compensating for phase artifacts in the conformal image and the second image. When alignment data is available the method aligns the conformal image and the second image prior by rotating either the conformal image or the second image through a rotation obtained from the alignment data. When alignment data is not available rotating either the conformal image or the second image through a sample rotation. The method obtains a correlation image x y based on

In another embodiment compensating for phase artifacts comprises removing the artifacts via deconvolution. In another embodiment compensating comprises multiplying a frequency domain image of the conformal image by a frequency domain point spread function of the second image and multiplying a frequency domain image of the second image by a frequency domain point spread function of the conformal image.

In another embodiment grazing angle compensation comprises scaling a pitch of each echo forming the conformal image and the second image by a secant of an angle between the echo and the surface reflecting the echo.

In one embodiment a system for correlating coherent images comprises a first sonar transmitter receiver and a second sonar transmitter receiver. The transmitter receivers have overlapping frequencies and observe terrain from overlapping aspects. The system also comprises a processor in communication with the transmitter receivers and a processor program product disposed on a processor readable medium and having instructions for causing the processor to compensate the images for grazing angle and to correlate the images.

In another embodiment the processor program product has further instructions for compensating for phase artifacts in the first and second transmitter receivers. The instructions cause the processor to multiply a frequency domain image of a first one of the images by a frequency domain point spread function of the second one of said images and multiply a frequency domain image of the second one of the images by a frequency domain point spread function of the first one of the images.

In another embodiment the instructions for causing the processor to compensate for grazing angle comprise instructions for causing the processor to scale a pitch of each echo forming the images by a secant of an angle between the echo and the terrain.

Referring now to there is shown a block diagram of method for implementing coherent image correlation. At blocks and the first and second images to be correlated are chosen respectively. It can be understood that in real time operation of method choosing images at blocks and is equivalent to forming images.

In order for images to correlate the subject terrain needs to be observed over the same horizontal aspects. Observing the subject terrain over the same horizontal aspects can be achieved by forming an image that conforms to the open closed aperture theorem meaning that all points in the image are observed over the same range of angles. This requires a fixed angular aperture rather than a fixed spatial aperture.

Alternatively the angular aperture can vary provided that there is a core angular aperture that is contained for all points. In this scenario the core angular aperture provides the basis for correlation the additional angular aperture simply provides enhanced resolution should the correct correlation occur at a location in the images where they both contain additional overlapping angular aperture. If all points in the images are formed using angular apertures with some overlapping extent the images will correlate. Images that conform to the open closed aperture theorem are typically formed by broadside squinted or circular Synthetic Aperture Sonars SAS s .

Block determines if at least one of the images has been formed using the open or closed aperture theorem. If not block discards one image and returns to block to chose or form another image until at least one image is so formed. If one image is formed by the open or closed aperture theorem the other image can be either a real aperture or SAS image.

The simplest case is correlating two open closed aperture images. In this case all points in the images are observed with the same set of angles and frequencies. The more advanced case concerns correlating an open closed aperture image with a real aperture image. Each point in the real aperture image will only be observed from one vantage point but the images will still correlate if the open closed aperture image has information about the appropriate aspects for each point. The real aperture correlation will be lower but it will still correlate.

Once two images of an image pair for correlation are chosen or formed the images are grazing angle compensated at block . As used herein grazing angle is defined as the angle between the sound impinging on the sea floor and the sea floor itself. It is the angle between a ray connecting the sonar to a point on the sea floor and a ray tangent to the sea floor at that point. When looking at the horizon the grazing angle would be zero. When looking straight down at the seafloor the grazing angle is 90 .

On a flat bottom at a constant altitude grazing angle varies with range. At a constant horizontal range grazing angle changes as the vertical position of the sonar is varied. For a contoured bottom changes in the bottom slope can also affect the grazing angle. With prior knowledge of the shape of the seafloor i.e. flat or whatever contours are extracted by a bathymetric sonar it is possible to accommodate variations in the vertical angle. By modeling the bottom as a manifold with embedded point scatterers it is possible to use grazing angle compensation to compensate for differences in the grazing angle.

Grazing angle compensation scales the pitch of the echo by the secant of the grazing angle. For instance if a patch of terrain was observed on the horizon grazing angle 0 and then observed at a grazing angle of 60 grazing angle compensation would predict the second echo to be one octave higher than the first. Grazing angle compensation allows for correlation of terrain observed at different grazing angles.

Once the image pair is grazing angle compensated aspect compensation is performed at block . It is known to those of skill in the art that transmitters receivers can introduce different phase artifacts into the images. It may not be possible to correlate the images without compensating for those artifacts. These artifacts can either be removed or equalized. Removing the artifacts via deconvolution is ideal. However deconvolution can be problematic since it involves a frequency domain division and some of the terms can be extremely small.

Method utilizes aspect compensation at block such that both images have the same artifacts. Aspect compensation is preferred since it involves frequency domain multiplication instead of the frequency domain division involved in deconvolution and because the resulting images have common zero regions in the frequency domain.

Considering two images of a scene F x y the expected images are be I x y F x y P x y and I x y F x y P x y where P x y and P x y are the respective point spread functions for the two images. In the frequency domain this would be I k k F k k P k k and I k k F k k P k k . For aspect compensation each frequency domain image is then multiplied by the frequency domain point spread function of the other image such that the two images of the image pair are equivalent I k k P k k I kk P kk .

Aspect compensation can safely equalize the images for correlation. After aspect compensation the two images will have non ideal point spread functions due to phase artifacts but those are removed by the correlation process. While removing or equalizing sonar artifacts through aspect compensation improves correlation performance those of skill in the art can recognize that correlation can be performed without aspect compensation. Accordingly block is illustrated in phantom in .

Once the images of the image pair are grazing angle and aspect compensated block determines if alignment data is available for the images. If alignment data is available the images can be rotated by the known rotation at block such that they are aligned noting that no rotation is necessary if the alignment data indicates the images are already aligned. Accordingly block is illustrated in phantom in . If alignment data is not available a range of possible rotations and a sampling rate can be defined at block and a test image pair is formed for each rotational sample at block .

The sampling rate can depend on the resolution desired for correlation with greater resolution being obtained the smaller becomes. As an example it may be known that the images were formed over no more than two quadrants. Hence the range of possible rotations can be defined as 0 to 180 with a sampling rate 5 . Thus test image pairs are formed for 0 5 10 . . . and 180 . If greater resolution is desired a sampling rate of 1 can be defined with test image pairs formed for 0 1 2 3 . . . and 180 .

At block the image pair or test image pair if rotational sampling is needed is correlated by calculating the correlation coefficient corresponding to each possible image shift x y to obtain a correlation image x y based on the known relationship 

As is known in the art such calculations can be carried out in a number of ways without limitation to method . For example but not for limitation the calculations can be carried out by convolving the images and squared images with appropriately sized matrices of ones or by multiplying their Fourier transforms against the Fourier transforms of appropriately sized matrices containing masks of ones. Zero padding can be used in the latter case to prevent circular convolution effects.

If the image pair is not a test image pair as determined at block the correlation image can be output to the user at block . Method can end or return to block to choose further images as determined at block .

If the image pair is a test image pair and is not the last in the series of image pairs as determined at block is incremented block to obtain the corresponding next one of the image pairs and method proceeds to block . If there are no further image pairs as determined at block the correlation image containing the highest correlation coefficient from the set of correlation images obtained from the test image pairs is chosen at block and method proceeds to block .

Optionally as shown in phantom at block the correlation image corresponding to each image pair can be output to the user. Also optionally the image shift corresponding to the peak correlation coefficient can be output as indicated in phantom at block .

Referring now to there is shown a system having a sonar transmitter receiver for forming sonar images. Sonar transmitter receiver is in communication with processor and image data from transmitter receiver is input to processor for implementation of method . Processor can accept sonar image data from additional transmitters receivers or sonars one of which is shown in designated as reference number .

As described previously with respect to method the images chosen for correlation can be chosen from images stored in processor or from real time image data as the images are formed by transmitters receivers and . For images to be correlated the images are to be formed by sonars such as sonar transmitters receivers and having overlapping frequencies that observe terrain from overlapping aspects as illustrated by arcs in . It will be apparent to those of skill in the art that sonar can represent sonar displaced in time and location.

What have thus been described are systems and methods for coherent image correlation which include sonars with overlapping frequencies that observe terrain from overlapping aspects to form sonar images. The method is implemented on a processor which can store images received from the sonars or can process image data in real time as the images are formed.

First and second sonar images are chosen from the stored images and or from the real time images at least one of which is formed using the open or closed aperture theorem. The images are grazing angle compensated and if they are not aligned a range of possible rotations can be defined and image pairs can be created for a sampling of rotational angles. In addition the images can be aspect compensated to remove windowing and beam pattern effects if necessary.

Once both images are grazing angle compensated and aligned the correlation coefficient for each possible image shift is calculated to obtain a correlation image. If the images were not aligned the alignment angle can be obtained from the correlation image of the sampling containing the highest correlation coefficient. Optionally the image shift corresponding to the peak correlation coefficient can be provided.

Obviously many modifications and variations of the present invention may become apparent in light of the above teachings. For example the systems and methods described herein can be used with radar images.

The ability to correlate sonar or radar images is important for a multitude of applications. According to the open closed aperture theorem it is possible to fuse information from separate synthetic aperture passes to form a larger higher resolution synthetic aperture. Coherent image correlation enables this as it allows images to be co registered for coherent fusion.

Likewise coherent correlation allows for mosaicking and multi pass image fusion for speckle reduction. Overlapping images can be stitched together mosaicked once they are co registered. If the same scene is observed multiple times the images can be fused to reduce speckle once they are co registered.

Additionally coherent correlation also allows for high resolution navigation. For instance a survey performed with a synthetic aperture sonar can be used as a prior map for secondary robots with inexpensive real aperture sonars. Also coherent correlation can be used for object recognition by comparing sonar images to libraries of known targets.

Further coherent correlation can be used for change detection. Images of terrain can be co registered and correlated on a patch by patch basis. Patches of the sea floor that no longer correlate with prior imagery can be flagged for further inspection. Coherent correlation can also be used for multi image focusing. Synthetic aperture sonar images often degrade due to vehicle surging. The signals from individual sonar elements from one synthetic array can be correlated against a second synthetic aperture image to estimate such along track motion.

It will be understood that many additional changes in details materials and arrangements of parts which have been described herein and illustrated in order to explain the nature of the invention may be made by those skilled in the art within the principle and scope of the invention as expressed in the appended claims.


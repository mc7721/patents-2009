---

title: Method and apparatus to minimize antenna backside signal response and ambiguity
abstract: Method and apparatus for minimizing antenna backside signal response and ambiguity in low frequency applications, particularly low frequency synthetic aperture radar (SAR). Various time delay elements are selectably switched into the signal path so as to cause a null to be placed in the antenna response pattern in the direction of undesired radar returns. The means for selectably switching may be dithered so as to introduce modulation onto the undesired radar return to aid in the discrimination and removal of the undesired radar return from the SAR image during post processing.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08013792&OS=08013792&RS=08013792
owner: The United States of America as represented by the Secretary of the Air Force
number: 08013792
owner_city: Washington
owner_country: US
publication_date: 20090806
---
This patent application claims the priority benefit of the filing date of provisional application Ser. No. 61 192 323 having been filed in the United States Patent and Trademark Office on Sep. 17 2008 and now incorporated by reference herein.

The invention described herein may be manufactured and used by or for the Government for governmental purposes without the payment of any royalty thereon.

This invention relates generally to the field of radar. More specifically the present invention relates to synthetic aperture radar SAR .

The operation of SAR is a side looking process. This is due to the fact that one axis of the imaging process is the radar range and the imaging process effectively collapses in the range direction of the antenna aperture which is downward looking. Any response from energy in the downward direction is eliminated by range gating i.e. the elimination of the signal by exclusion of certain time periods in the receive window . For many microwave SAR systems the antenna pattern is directional enough that the combination of range gating and pattern amplitude is sufficient for good imaging.

Microwave SAR systems are however limited in their capability to identify targets through obstruction such as foliage. Therefore one must look to lower frequency imaging systems for effective penetration. On the other hand VHF SAR is useful because it is low enough in frequency to operate through foliage. But as the frequency of operation drops to the VHF range the size of the typical antenna is electrically too small to achieve a pattern that is very directional therefore range gating no longer suffices to ensure good imaging.

The fundamental problem lies in the fact that electrically small apertures produce near omni directional beam patterns. Omni directional beam patterns cause a multitude of reflection back into the radar at the same ranges as the desired target. These are impossible to eliminate by range gating because they will pass through the same range gate as the intended target image. What is lacking in the prior art is either a method or apparatus which can provide good SAR imaging at lower i.e. VHF frequencies.

The present invention provides a method and apparatus to minimize antenna backside signal response and ambiguity.

The present invention therefore results in a method and apparatus to minimize antenna response to received signals originating from undesired directions.

It is therefore an object of the present invention to provide a method and apparatus to eliminate the ambiguity that received signals originating from undesired directions cause.

It is a further object of the present invention to provide a method and apparatus to introduce response nulls anywhere into an antenna response pattern.

It is yet still a further object of the present invention to provide a method and apparatus to detect and discriminate received signals originating from undesired directions.

An additional object of the present invention is to provide a method and apparatus to process a SAR image in a manner that reduces the effect of received signals originating from undesired directions thereon.

Briefly stated the present invention provides a method and apparatus for minimizing antenna backside signal response and ambiguity in low frequency applications particularly low frequency synthetic aperture radar SAR . Various time delay elements are selectably switched into the signal path so as to cause a null to be placed in the antenna response pattern in the direction of undesired radar returns. The means for selectably switching may be dithered to as to introduce modulation onto the undesired radar return to aid in the discrimination and removal of the undesired radar return from the SAR image during post processing.

The above and other objects features and advantages of the present invention will become apparent from the following description read in conjunction with the accompanying drawings in which like reference numerals designate the same elements.

As described in the Background of the Invention range gating cannot be used to eliminate energy from the same range in the backwards direction at low frequencies. This ambiguity can only be eliminated though spatial methods such as antenna pattern control. The present invention therefore provides a method and apparatus that creates a broadband null in the backwards direction of an antenna pattern at low frequencies.

Fundamentally the prior art teaches how to place a null at a predetermined position in an antenna radiation pattern. But it does not teach what is necessary to effectively cancel false ambiguous imaging from a low frequency SAR. What is yet needed and is provided by the present invention is an apparatus and method for isolating ambiguous imaging from desired imaging notwithstanding the position of the forced null nor its width. Therefore the preferred embodiment of the present invention employs switching between two or more time delay elements so as to cause two or more nulls placed in two or more positions. The present invention creates several slightly displaced nulls within respective antenna patterns and scans received energy over them. The invention then processes this energy and determines the differences between respective antenna patterns. From this the present invention can determine energy from desired image scan angles from ambiguous energy entering the antenna from the same range but undesired angle.

Referring to the preferred embodiment of the present invention creates two null positions though the addition of a first switch and a second switch on either side of a first time delay and a second time delay . Switching allows placement of the null in either of two different locations in the antenna beam pattern. While two discrete time delay elements are depicted there is no limitation to the number of discrete nulls that can be created because there is no limitation to the number of time delays or switches that can be employed to switch time delays in or out of the path between the signal source and antenna radiating elements. Processor runs a software program which controls the switching of first switch and second switch . First time delay and second time delay may be discrete time delay elements such as coaxial or waveguide sections of transmission line. However the invention is not limited to the incorporation of fixed time delay elements. Variable time delays may be employed where they are of sufficiently broad bandwidth. The invention may also forego switches where variable time delay is used.

Referring to shows that while the switching of the null position does induce some modulation on the antenna main beam it is minimal. Nearly all i.e. 80 of switching induced modulation on the main beam can be removed by processing as depicted in .

However and still referring to indicates that significant modulation occurs in the vicinity of the null position as the null is switched between two discrete positions. Herein lies the benefit of the present invention in discriminating energy from desired targets from energy from undesired ambiguous targets at the same range. The switching of the nulls produces a scintillation effect attributed to switching the null position. The modulation of the amplitude response caused by switching the null position i.e. apparent scintillation in the ambiguous targets is detected in a computer processor which in turn tags radar returns having this modulation as ambiguous. Whereas desired radar returns will enter the main beam will not exhibit these modulation effects and will be tagged as desired returns.

Referring to and shows that the null region in the antenna pattern can increase in width i.e. angular coverage so as to better focus the null in the direction of the ambiguous radar returns and enhancing the rejection of these undesired returns.

Processor see implements a software program that integrates a large number of radar return pulses from a desired direction to form a SAR image. Integration is required because even for targets in the desired direction there can exist wide amplitude variations in the returns. Moreover radar returns from targets in the undesired direction while attenuated by the effect of the positioning of the null may still have greater amplitude than returns for the desired direction. These returns from the undesired direction can produce artifacts in the SAR image formed from the desired antenna direction. One skilled in the art would appreciate that processor would normally function in cooperation with a receiver and that such a receiver would detect certain signal characteristics i.e. modulation signal strength etc. which processor in combination with a software program would in turn exploit so as to render an improved SAR image. In that regard processor will 1. broaden the null in this undesired direction to reduce the amplitude of undesired radar returns causing the artifacts 2. detect the modulation induced on returns from the undesired direction and identify artifacts in the SAR image and 3. subtract these artifacts from the fully formed SAR image.

Having described preferred embodiments of the invention with reference to the accompanying drawings it is to be understood that the invention is not limited to those precise embodiments and that various changes and modifications may be effected therein by one skilled in the art without departing from the scope or spirit of the invention as defined in the appended claims.


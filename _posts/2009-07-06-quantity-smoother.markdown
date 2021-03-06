---

title: Quantity smoother
abstract: In an embodiment, a quantity smoother includes a first stage and a second stage. The first stage is operable to receive a sequence of raw samples of a quantity and to generate from the raw samples intermediate samples of the quantity, the intermediate samples having a reduced level of fluctuation relative to the sequence of raw samples. The second stage is coupled to the first stage and is operable to generate from the intermediate samples resulting samples of the quantity, the resulting samples having a reduced level of fluctuation relative to the sequence of intermediate samples. For example, such a quantity smoother may be part of a target-ranging system on board a fighter jet, and may smooth an error in an estimated target range so that the fighter pilot may more quickly and confidently determine in his head a range window within which the target lies.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08164510&OS=08164510&RS=08164510
owner: BAE Systems Information and Electronic Systems Integration Inc.
number: 08164510
owner_city: Nashua
owner_country: US
publication_date: 20090706
---
The present application is a Continuation In Part of copending U.S. patent application Ser. No. 12 364 480 filed Feb. 2 2009 which application claims priority to U.S. Provisional Application Ser. Nos. 61 063 251 61 063 290 61 063 271 and 61 063 207 filed on Jan. 31 2008. All of the foregoing applications are incorporated herein by reference in their entireties.

The invention was made with United States Government support under Contract No. N00019 02 C 3002. Accordingly the United States Government has certain rights in this invention.

This Summary is provided to introduce in a simplified form a selection of concepts that are further described below in the Detailed Description. This Summary is not intended to identify key features or essential features of the claimed subject matter nor is it intended to be used to limit the scope of the claimed subject matter.

In an embodiment a quantity smoother includes a first stage and a second stage. The first stage is operable to receive a sequence of raw samples of a quantity and to generate from the raw samples intermediate samples of the quantity the sequence of intermediate samples having a reduced level of fluctuation relative to the sequence of raw samples. And the second stage is operable to generate from the intermediate samples smoothened samples of the quantity the sequence of smoothened samples having a reduced level of fluctuation relative to the sequence of intermediate samples.

For example such a quantity smoother may be part of a target ranging system on board a fighter jet. A ranging portion of the system may recursively estimate the range of the target from the jet and generate samples of a raw error in the range estimate. And the smoother may smoothen the raw error samples so that the fighter pilot may more quickly determine from the samples a range window within which the target lies.

Geometrically speaking the target T lies in an elevation plane which is perpendicular to the jet azimuth plane and which includes the straight line along which His measured. For example in this embodiment the elevation plane may be coincident with the page of .

Referring to the fighter jet typically includes a targeting system not shown in for detecting the target T and for determining one or more of the following targeting parameters R H and V. For example the targeting system may actively detect and range i.e. determine Rfor the target T by transmitting a signal e.g. a radar signal that impinges upon and that is reflected back to the jet by the target T and by receiving the reflected signal with a directional antenna not shown in . The targeting system may then determine and by analyzing the phase of the received signal at each of multiple elements of the antenna. Alternatively the targeting system may passively detect and range the target T by similarly analyzing a signal emitted by the target T to determine and . Passive detection may be useful when the pilot of the fighter jet does not want to alert the personnel manning the target T to the jet s presence or when the target is a pop up target e.g. a hand held rocket launcher that is difficult or impractical to actively detect. Because such target detecting and ranging systems are known the details of such a system are omitted for brevity.

Referring again to although the target detecting and ranging system onboard the fighter jet can determine from and that the target T lines along a straight line path the system cannot determine from these angles alone a value for R H or V.

Therefore the targeting system onboard the jet needs additional information to determine at least one of R H and V. Once the targeting system determines a value for at least one of these parameters it can determine the value for the remaining ones of these parameters via a trigonometric identity such as the law of sines.

For example a targeting system employing passive detection may obtain this additional information by comparing a signature of a signal emitted from the target T with signal signatures that are stored in a database. If the signature of the emitted signal matches a signature in the database then the targeting system may be able to identify the target T and may be able to retrieve from the database information describing the target or the emitted signal. For example if the database includes a lookup table that effectively plots distance vs. signal to noise ratio SNR for the emitted signal then the targeting system may calculate a value for Rby measuring the SNR of the emitted signal at the fighter jet and obtaining a value for Rfrom the lookup table.

Alternatively if the target detecting and ranging system determines that the target T is a type of ground based target e.g. a tank or rocket launcher then if the target is at sea level Vis substantially equal to the altitude of the fighter jet because the altitude is measured by an altimeter not shown in on board the jet the targeting system has access to the altitude. Once the targeting system has a value for V the system can calculate values for Hand Rusing for example the law of sines.

In yet another alternative the targeting system may instruct the pilot to manoeuvre the jet so as to significantly change at least the azimuth angle from measurement point to measurement point and then locate T at the intersection of the multiple Hlines at these different angles . Such a technique is described in U.S. Pat. No. 7 132 961 which is incorporated by reference.

In still another alternative the targeting system may obtain azimuth and elevation angles and from a second object such as a second fighter jet and determine the location of the target T using and from the second object and and from the jet . Such a technique is described in U.S. patent application Ser. No. 12 364 480 which is incorporated by reference.

With any of the above described targeting techniques the targeting system may calculate one or more of the target parameters R H and Vrecursively over a period of time. Taking Rfor example the targeting system may calculate an initial sample for Rthat has a value of relatively low accuracy and then may calculate successive samples for Rusing one or more of the previous samples such that over a period of time e.g. 1 60 seconds the samples of Rconverge toward a steady state value that has a higher accuracy for example an accuracy within approximately 5 .

In addition the targeting system may calculate a percent parameter error PPE for one or more of these parameters. Taking Rfor example the targeting system may calculate an initial sample of a percent range error PRE in R this initial sample having a relatively high value and may then calculate successive samples of PRE each of the samples of PRE corresponding to a respective sample of R. Over a period of time e.g. 1 60 seconds as the samples of Rconverge toward a more accurate steady state value the samples of PRE converge toward a lower steady state value. Therefore an observer such as a pilot may interpret the convergence of the PRE samples toward a lower value as indicating that the samples of Rare converging toward a more accurate value.

The targeting system may display to the pilot of the jet the sequences of samples calculated for a targeting parameter and its corresponding PPE so that the pilot can use these samples to make a flight decision. For example the pilot may monitor the samples of Rand PRE to determine when the target T is in range of a missile with which the jet is armed.

Because a pilot may have only a short period of time e.g. a few seconds to make a decision e.g. evade or destroy regarding a target T the targeting system may provide to the pilot targeting parameters and corresponding PPEs that are sufficient to allow the pilot to make an informed decision within a specified time.

It is theorized that a pilot can more confidentially make mental calculations involving the parameter and PPE samples and thus can more quickly make decisions based on the parameter and PPE samples if at least the PPE samples converge toward a steady state value in a smooth and relatively monotonic manner. Referring to Table I an example of Rand PRE converging smoothly and monotonically is discussed.

In this example the jet is carrying a missile with a range of 25 nautical miles and the pilot would like to fire the missile at the target T as soon as the target is in range.

So at an initial time t the targeting system displays an initial value of 30 nautical miles for R and an initial PRE of 50 . This allows the pilot to mentally calculate that the target T is within a range window that is between approximately 15 and 45 nautical miles from the jet . Because this range window extends beyond the missile range of 25 nautical miles the pilot realizes that if he fires the missile at this time then the missile may be unable to reach and destroy the target T.

Similarly at a second time t the targeting system displays a value of 27 nautical miles for R and a PRE of 35 . This allows the pilot to mentally calculate that the target T is between approximately 18 and 36 nautical miles from the jet . Because this range window extends beyond the missile range of 25 nautical miles the pilot realizes that if he fires the missile at this time then the missile may be unable to reach and destroy the target T. But the pilot has information sufficient to realize that the maximum range is getting smaller a decrease from 45 to 36 nautical miles .

At a third time t the targeting system displays a value of 25 nautical miles for R and a PRE of 25 . This allows the pilot to mentally calculate that the target T is between approximately 18 and 31 nautical miles from the jet . Because this range window extends beyond the missile range of 25 nautical miles the pilot continues to realize that he should not yet fire the missile. But the pilot also has information sufficient to see that the maximum range is continuing to get smaller a decrease from approximately 36 to 31 nautical miles .

At a fourth time t the targeting system displays a value of 23 nautical miles for R and a PRE of 17 . This allows the pilot to mentally calculate that the target T is between approximately 19 and 27 nautical miles from the jet . Because this range window still extends beyond the missile range of 25 nautical miles the pilot continues to realize that he should not yet fire the missile. But the pilot has information sufficient to see that the maximum range continues to get smaller a decrease from approximately 31 to 27 nautical miles .

Finally at a fifth time t the targeting system displays a value of 22 nautical miles for R and a PRE of 10 . This allows the pilot to mentally calculate that the target T is between approximately 20 and 24 nautical miles from the jet . Because the maximum value of this range window is less than 25 nautical miles and because the range window has converged relatively smoothly and monotonically from t t the pilot has information sufficient to be confident that the target T is in range of the missile and that he can now fire the missile.

Unfortunately a targeting system may generate target parameter and or PPE samples that do not converge to respective steady state values relatively smoothly and monotonically and this uneven convergence may potentially increase the time required by a pilot to make a decision regarding a target.

That is the targeting system may generate target parameter and or PPE samples that oscillates sometimes wildly until they eventually converge toward a steady state value. For example such oscillating in the PRE samples may cause the window for Rto grow significantly then shrink significantly then grow significantly and so on. As an analogy in this example the target system is generating the PRE samples in an under damped manner such that the PRE samples ring much like an electrical signal generated by a circuit with an under damped transient response may ring. 

And this oscillation of the target parameter and or PPE samples may make it more difficult for the pilot to make mental calculations involving these samples and may increase the time before the pilot feels confident that a particular target parameter is within a particular window e.g. that the target parameter Ris within a window that indicates that the target is within the range of a missile .

The first stage receives a stream of raw quantity samples and generates from the raw samples a stream of intermediate samples that have a lower level of oscillation than the raw samples. For example the first stage may be a low pass type of filter having a latency. Generally the latency is the number of samples received by the first stage before the first stage generates a first intermediate sample and is dependent on the filtering algorithm. In an embodiment the first stage may be a median filter as discussed below in conjunction with .

The second stage receives the stream of intermediate samples from the first stage and generates from the intermediate samples a stream of smoothened samples that have a lower level of oscillation than the intermediate samples and that are more monotonic than the stream of raw samples. For example the second stage may be a curve fitter that fits the intermediate samples to one or more curves that generates the smoothened samples from the one or more curves and that has a latency. In an embodiment the second stage fits received samples to one or more fifth order polynomials as discussed below in conjunction with .

Still referring to alternate embodiments of the quantity smoother are contemplated. For example although described as having two stages the smoother may have more or fewer than two stages and these stages may each operate according to any algorithm suitable to aid in sample smoothing. Furthermore although shown coupled in series the stages of the smoother may be coupled in parallel or some of the stages may be coupled in parallel and some of the stages may be coupled in series.

In addition to the quantity smoother the targeting system includes an antenna signal processor quantity estimator a raw percent error determiner and a display .

The targeting system may be disposed in one of a variety of locations. For example the system may be disposed in a vehicle such as a fighter jet tank ship or space craft in a portable base station such as a portable missile launcher or in a permanent base station.

The antenna is operable to receive at least one signal that carries information indicative of a location of a target. If the targeting system is actively detecting and ranging a target such signals may include radar signals that are reflected by the target to the antenna . These radar signals may originate from the antenna or from another antenna not shown associated with the targeting system such as another antenna mounted to the vehicle in which the targeting system is disposed. In contrast if the targeting system is passively detecting and ranging a target such signals may include signals that are emitted from or reflected by the target itself. Antennas suitable for use as the antenna and techniques for actively and passively detecting and ranging a target are known. An example of a known technique for passively detecting and ranging a target is disclosed in U.S. Pat. No. 7 132 961 which is incorporated by reference.

The signal processor extracts from the at least one signal received by the antenna information indicative of the location of the target and converts this information into raw data. For example the signal processor may determine the instantaneous azimuth and elevation angles and at which the received signal is incident to the antenna may determine the type and instantaneous strength of the signal and then may convert the angles signal type and signal strength into raw data samples. The signal processor may also determine the altitude of the vehicle carrying the targeting system and convert the altitude into additional raw data samples. The signal processor may continually process the received signal and determine the vehicle altitude over a period of time and periodically update the raw data samples. For example the signal processor may generate raw data samples for the azimuth angle the elevation angle the signal strength and the vehicle altitude once every second. Furthermore the signal processor may be implemented in hardware software or in both hardware and software.

The parameter estimator estimates from the raw data a stream of samples for one or more estimated target parameters TP. Examples of such estimated target parameters TPinclude azimuth angle elevation angle horizontal range vertical range and actual range. The parameter estimator may be implemented in hardware software or in both hardware and software.

The parameter estimator may estimate the TPsamples recursively and this recursive estimation may cause the samples to oscillate as discussed above.

For example the parameter estimator may estimate a first set of X Y Z coordinates for the target based on a first set of raw data from the signal processor and then generate an estimated sample for target parameter R range to target based on this first set of coordinates.

Next the estimator may estimate a second set of X Y Z coordinates for the target based on a second set of raw data samples from the processor .

Then the estimator may estimate a first hybrid set of X Y Z coordinates based on the first and second sets of coordinates. For example the estimator may average the first and second sets of coordinates to generate the first hybrid set of coordinates although the estimation algorithm may be more complicated than this.

Next the estimator generates a second estimated sample of Rbased on the first hybrid set of coordinates.

Then the parameter estimator generates subsequent estimated samples for Rtaking into account the current set of estimated target coordinates X Y Z and at least some of the previous sets of estimated coordinates X Y Z.

These subsequent estimated samples for Reventually converge toward or to a steady state value of R the accuracy of which depends on the error introduced by the antenna the channel over which the signal received by the antenna propagates the processor and the estimator . Of course if the target system is in a moving vehicle if the ranged target is moving or if both the vehicle carrying the target system and the ranged target are moving relative to each other then the steady state value of Rwill change based on this movement but with reduced or no oscillation after the convergence period.

There are conventional algorithms that the parameter estimator may employ to estimate target parameters. For example U.S. Pat. No. 7 132 961 which is incorporated by reference discusses a target parameter estimator that employs a Kalmann algorithm.

Still referring to the raw error determiner estimates for each stream of TPsamples a respective stream of samples for the raw percentage parameter error PPE in each TP. That is each sample of a PPEstream corresponds to a respective sample of a respective TPstream. The determiner estimates each sample of a PPEstream from the corresponding sample of a corresponding TPstream and from information representative of the errors introduced into the TPsamples by for example the antenna the channel over which the signal received by the antenna propagates the processor and the estimator . Furthermore the raw error determiner may be implemented in hardware software or both hardware and software.

More specifically the raw error determiner includes an accuracy determiner and a raw percent parameter error PPE calculator .

For each sample in a stream of TPsamples the accuracy determiner determines a respective 1 sigma sample which is the statistical standard deviation for the corresponding sample of TP. Therefore the determiner generates a stream of samples of where each sample corresponds to a respective sample of TP. Algorithms and techniques for calculating the samples are known and therefore further discussion of the calculation of the samples is omitted for brevity.

For each sample of the raw PPE calculator calculates a corresponding sample of PPEaccording to the following equation 100 1 

Still referring to the quantity smoother smoothens the PPEsamples by reducing or eliminating the oscillation in these samples. That is the smoother acts to dampen this oscillation in a manner similar to that discussed above in conjunction with . Furthermore the quantity smoother may be implemented in hardware software or both hardware and software.

In an embodiment the first stage of the quantity smoother includes a filter and the second stage includes a curve fitter .

The filter receives the PPEsamples from the error determiner and generates from these samples a stream of samples PPE which converge toward a steady state value more smoothly and more monotonically than the PPE samples. For example the filter may be a median filter. The operation of an embodiment of the filter is discussed below in conjunction with .

The curve fitter receives the samples PPE and generates from these samples a stream of samples PPE which converge toward a steady state value even more smoothly and more monotonically than the PPEsamples do. The curve fitter does this by fitting the PPEsamples to one or more known curves and by then generating the PPEsamples from this curve these curves.

More specifically in an embodiment in response to each sample of PPEfrom the filter the curve fitter fits this and all previous samples of PPEto a best fit curve and then generates a sample of PPEfrom this curve this sample of PPEcorresponding to the most recent sample of PPE. Because the best fit curve may be different for each sample of PPE the curve fitter may fit each sample to a different curve. For example where it is known that the PPEsamples converge approximately according to a decaying exponential then the curve fitter may fit the values of PPEto a fifth order polynomial. In response to each sample of PPE the curve fitter may alter the coefficients of this polynomial to achieve the best curve fit. The operation of an embodiment of the curve fitter is discussed below in conjunction with .

The display successively displays to the pilot or other observer each sample of TPwith a corresponding sample of PPE for example in a display format similar to that of Table I above. That is the display displays to the pilot the most recent sample of TPand the corresponding most recent sample of PPE and updates these samples as they are generated by the quantity estimator and the quantity smoother respectively of course the targeting system may have to delay the TPsamples to account for the latency of the quantity smoother . This allows the pilot to perceive the PPEvalues converging toward a steady state value relatively monotonically and with little or no oscillation and thus may allow the pilot to more quickly determine when the value of TPis within a particular window for example when a range to a target indicates that the target is within missile range .

Still referring to alternate embodiments of the targeting system are contemplated. For example as mentioned above although shown as smoothing only a single stream of PPEsamples the system may smoothen additional streams of PPEsamples may smoothen one or more streams of TPsamples or may smoothen streams of PPEsamples and TP. Furthermore the quantity smoother may be designed as part of the original targeting system or may be installed as an add on to an existing targeting system.

Referring to the operation of an embodiment of the targeting system of is discussed where the system is disposed on a fighter jet such as the fighter jet of and where the system estimates the range to a target and the percentage error in the estimated range.

Referring to the parameter estimator begins generating samples of R plot at time t t 0 seconds and in this embodiment subsequently generates a new sample t t n once every second. The samples of Rconverge substantially to the actual range plot after about forty seconds. But as discussed above in some circumstances a pilot may need to make a decision e.g. destroy the target evade the target regarding the ranged target within a time that is significantly less than forty seconds for example within ten seconds.

Referring to the error determiner also begins generating samples of PREat time t and in this embodiment subsequently generates a new sample every second. Although these samples converge toward a steady state value of approximately 5 they do so non monotonically and they continue to oscillate even at fifty seconds which may be beyond the time within which the pilot would like to make a decision regarding the target.

Referring to the filter generates samples of PREevery second. One can see that the samples of PREare more monotonic and barely oscillate as compared to the samples of PRE .

Referring to and the operation of an embodiment of the filter is described where the filter implements a one dimensional median filter function.

A one dimensional median filter may include two or more parallel first in first out FIFO buffers each having a length L. The samples to be filtered are shifted into the first FIFO one at a time such that the sample to be filtered is at the center location of the first FIFO if L is an odd number and the sample to be filtered is in one of the two center locations of the first FIFO if L is an even number. For samples at the beginning or end of a sample stream zeros may be used to fill the empty locations of the FIFO. Next the samples are reordered from lowest to highest value and then parallel loaded from the first FIFO into the second FIFO. The filtered sample generated by the filter equals the sample in the center location of the second FIFO if L is an odd number and equals the average of the two samples in the two center locations of the second FIFO if L is an even number. Then the next sample is shifted into the first FIFO and the procedure repeats.

For example purposes the operation of an embodiment of the filter is discussed in which the filter includes two parallel FIFO buffers having lengths L 7 the first FIFO is represented in the subsequent text by straight brackets the second FIFO is represented in the subsequent text by curved brackets and the first ten samples of PRE rounded to the nearest integer are decimal 26 29 23 13 14 9 12 9 7 and 8.

Initially at sample time t the first FIFO buffer is loaded from right to left with samples of PREas follows 

where the first sample 26 of PREis in the center location of the buffer and the leftmost three buffer locations are loaded with zeros. There is a latency of three samples because it is not until the fourth sample time tthat the first sample 26 is in the center location of the first FIFO buffer. But the targeting system makes this latency transparent to the pilot as discussed below in conjunction with . Furthermore to avoid confusion the plot of has not been shifted in time to show this latency. Therefore the sample of PREat sample time tin corresponds to the samples of Rand PREat the time tin respectively.

Next these samples are reordered from lowest to highest and loaded into the second FIFO buffer as follows 

Then the filter generates the first sample of PREequal to 13 which is the value of the sample in the center fourth location of the second FIFO buffer. This first sample 13 is plotted in at sample time t as stated above the plot of has not been time shifted to show the latency introduced by the filter .

Next at sample time t the next sample of PREis right shifted into the first FIFO buffer which in response to this shift has the following contents 

where the second sample 29 of PREis in the center location of the buffer and the leftmost two buffer locations are loaded with zeros.

Then these samples are reordered from lowest to highest and loaded into the second FIFO buffer as follows 

Next the filter generates the second sample of PREequal to 14 which is the value of the sample in the center fourth location of the second FIFO buffer. This second sample 14 is plotted in at time t.

Then at sample time t the next sample of PREis right shifted into the first FIFO buffer which in response to this shift has the following contents 

where the third sample 23 of PREis in the center location of the buffer and the leftmost buffer location is loaded with a zero.

Next these samples are reordered from lowest to highest and are loaded into the second FIFO buffer as follows 

Then the filter generates the third sample of PREequal to 14 which is the value of the sample in the center fourth location of the second FIFO buffer. This third sample 14 is plotted in at t.

Next at sample time t the next sample of PREis right shifted into the first FIFO buffer which in response to this shift has the following contents 

Then these samples are reordered from lowest to highest and are loaded into the second FIFO buffer as follows 

Next the filter generates the fourth sample of PREequal to 14 which is the value of the sample in the center fourth location of the second FIFO buffer. This fourth sample 14 is plotted in at t.

Then at sample time t the next sample of PREis right shifted into the first FIFO buffer which in response to this shift has the following contents 

Next these samples are reordered from highest to lowest and are loaded into the second FIFO buffer as follows 

Then the filter generates the fifth sample of PREequal to 13 which is the value of the sample in the center fourth location of the second FIFO buffer. This fifth sample 13 is plotted in at sample time t.

Next at sample time t the next sample of PREis right shifted into the first FIFO buffer which now has the following contents 

Then these samples are reordered from lowest to highest and are loaded into the second FIFO buffer as follows 

Next the filter generates the sixth sample of PREequal to 12 which is the value of the sample in the center fourth location of the second FIFO buffer. This sixth sample 12 is plotted in at sample time t.

Then at sample time t the next sample of PREis right shifted into the first FIFO buffer which now has the following contents 

Next these samples are reordered from highest to lowest and are loaded into the second FIFO buffer as follows 

Then the filter generates the seventh sample of PREequal to 9 which is the value of the sample in the center fourth location of the second FIFO buffer. This seventh sample 9 is plotted in at time t.

The filter continues operating in this manner to generate the eighth and higher samples of PREuntil the remaining PREsamples from the eighth sample onward are filtered.

Still referring to alternate embodiments of the filter are contemplated. For example the filter may have a length other than L 7. Generally the trade off is that smaller values of L introduce less latency but larger values of L provide a stronger filtering. Furthermore although shown as being loaded from the right the PREsamples may be shifted in from the left side of the first FIFO buffer. Moreover although described as reordering the samples in the first FIFO buffer and loading the reordered samples into the second FIFO buffer the samples may be reordered after they are loaded into the second FIFO buffer.

For each of these PREsamples the curve fitter fits the current and all prior samples to a fifth order polynomial that generally represents a decaying exponential. This polynomial may be a finite series expansion of e. For example this polynomial may include the first six terms of a Taylor or McClauren series expansion. Although the polynomial is always a fifth order polynomial in this example the curve fitter can change the curve defined by the polynomial by changing one or more of the coefficients of the polynomial.

Because a single PREsample can be fit to any curve the curve fitter may have a latency of for example three or four PREsamples. Because the curve fitter operates on the PREsamples from the filter the total latency of the quantity smoother is the sum of the latencies of the filter and the curve fitter. Therefore one may design the filter and curve fitter such that the latency of the quantity smoother is not greater than a specified latency. As discussed below the target system makes the latency of the quantity smoother transparent to the pilot by displaying only corresponding samples of TPand PPE Rand PREin the described example .

So for example purposes assume that the curve fitter requires at least three PREsamples to fit to a curve.

Therefore in response to the third sample 14 of PRE the curve fitter finds a first fifth order polynomial that best fits the first three samples 13 14 14 of PREusing a conventional curve fitting technique. For example the curve fitter may find the fifth order polynomial having the least mean square difference from the PREsamples or may use a Monte Carlo technique to find the best fit curve. Because these and other techniques for curve fitting are known a further discussion of how the curve fitter finds the best fit curve is omitted for brevity.

Next the curve fitter generates the third sample of PREequal to the value of the best fit curve at t which is the sample time corresponding to the third sample of PRE and the display displays the third sample of PREalong with the corresponding tsample of R. The curve fitter may also generate the first and second samples of PREfrom this same best fit curve although once the third sample of PREis generated it may be unnecessary to display the first and second samples of PREto the pilot via the display . But for purposes of illustration these first three samples of PREare plotted in at sample times t t and t respectively like the plot of the plot of has not been time shifted to show the latency introduced by the filter and curve fitter .

Then in response to receiving the fourth sample 14 of PRE the curve fitter finds a second fifth order polynomial that best fits the first four samples 13 14 14 14 of PRE. The second polynomial may or may not be the same as the first polynomial previously calculated as the best fit for the first three samples of PRE.

Next the curve fitter generates the fourth sample of PREequal to the value of the second polynomial at t which is the sample time corresponding to the fourth sample of PRE and the display displays the fourth sample of PREalong with the corresponding tsample of R. The fourth sample of PREis plotted in at time t.

Because the curve fitter has already generated the first second and third samples of PREfrom the first polynomial and these samples have already been displayed to the pilot on the display there is typically no need to update these first three samples using the second polynomial.

Therefore is not necessarily a plot of a single curve calculated by the curve fitter but may instead be a plot of the PREsamples generated from many curves calculated by the curve fitter up to one curve for each sample.

Then in response to receiving the fifth sample 13 of PRE the curve fitter finds a third fifth order polynomial that best fits the first five samples 13 14 14 14 13 of PRE. The third polynomial may or may not be the same as one of the previously calculated first and second polynomials.

Next the curve fitter generates the fifth sample of PREequal to the value of the third polynomial at t which is the sample time corresponding to the fifth sample of PRE and the display displays the fifth sample of PREalong with the corresponding tsample of R. The fifth sample of PREis plotted in at time t.

Then in response to receiving the sixth sample 12 of PRE the curve fitter finds a fourth fifth order polynomial that best fits the first six samples 13 14 14 14 13 12 of PRE. The fourth polynomial may or may not be the same as one of the previously calculated first second and third polynomials.

Next the curve fitter generates the sixth sample of PREequal to the value of the fourth polynomial at t which is the sample time corresponding to the sixth sample of PRE and the display displays the sixth sample of PREalong with the corresponding tsample of R. The sixth sample of PREis plotted in at time t.

Then in response to receiving the seventh sample 9 of PRE the curve fitter finds a fifth fifth order polynomial that best fits the first seven samples 13 14 14 14 13 12 9 of PRE. The fifth polynomial may or may not be the same as one of the previously calculated first second third and fourth polynomials.

Next the curve fitter generates the seventh sample of PREequal to the value of the fifth polynomial at t which is the sample time corresponding to the seventh sample of PRE and the display displays the seventh sample of PREalong with the corresponding tsample of R. The seventh sample of PREis plotted in at time t.

The curve fitter continues operating in this manner to generate the eighth and subsequent samples of PREuntil the remaining PREsamples from the eighth sample onward are fit to a respective curve.

Still referring to one can see that the samples PREoscillate even less than the PREsamples of and are significantly smoother than the PREsamples. Consequently the PREsamples may allow the pilot to make a decision regarding the target more quickly and with more confidence than if the pilot were relying on the PRE samples or even if the pilot were relying on the PREsamples. For example even if the pilot waits until the value of the PREsamples are below 10 he would have to wait only about seven seconds before he is able to begin making a decision regarding the target.

Referring to further alternate embodiments of the target system are contemplated. For example although described as generating samples of R PRE PRE and PREevery second the estimator calculator filter and curve fitter may respectively generate samples of these quantities at other intervals. Furthermore the target system may not display every set of samples on the display . For example the system may generate samples of Rand PREevery millisecond but may display samples of Rand PREon the display only once per second so that the pilot has time to discern and comprehend the samples and to determine a range window of a target from the samples. Moreover although described as including two stages the quantity smoother may include more or fewer than two stages. For example the smoother may include only the first stage with the filter and provide the samples PREdirectly to the display .

From the foregoing it will be appreciated that although specific embodiments have been described herein for purposes of illustration various modifications may be made without deviating from the spirit and scope of the disclosure. Furthermore where an alternative is disclosed for a particular embodiment this alternative may also apply to other embodiments even if not specifically stated.


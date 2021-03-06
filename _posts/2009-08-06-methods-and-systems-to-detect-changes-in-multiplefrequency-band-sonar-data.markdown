---

title: Methods and systems to detect changes in multiple-frequency band sonar data
abstract: Methods and systems to detect changes in a region of space relative to baseline measurements, including to process data to detect potential objects, or contacts against a natural background environment, to characterize and geo-register the contacts, to compare and correlate the contacts with a database of known objects, and to report uncorrelated contacts as new objects in the space. Features disclosed herein may be implemented to process image data from a line-by-line image-generation system including, for example, side-looking sonar. Methods and system may be implemented with respect to multi-frequency band sonar data.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08189428&OS=08189428&RS=08189428
owner: The Johns Hopkins University
number: 08189428
owner_city: Baltimore
owner_country: US
publication_date: 20090806
---
This application claims the benefit of U.S. Provisional Patent Application No. 61 086 559 filed on Aug. 6 2008 which is incorporated herein by reference in its entirety.

This invention was made with U.S. Government support under the Naval Sea Systems Command contract number N00024 03 D 6606. The U.S. Government has certain rights in the invention.

Methods and systems disclosed herein are directed to detection of changes in a region of space relative to baseline measurements including detection of changes in multiple frequency band sonar data.

Sonar images of an underwater area may be used to identify objects in the area. Subsequent sonar images of the area may be used to re identify objects in the area which may be compared to the previously identify objects. New objects may be presented to an operator for evaluation.

Sonar images of an underwater area may include relatively vast numbers of non overlapping target sized patches of seafloor any of which may include an object of potential interest. In some situations there may be a need to present newly identified objects for human evaluation in real time. The potentially vast quantity of data may however render it impractical for humans to detect objects in sonar images to correlate the detected objects with previously identified objects and to identify new objects in real time.

The U.S. Naval Research Laboratory of Washington D.C. has developed techniques as taught in U.S. Patent Publication No. 2009 0016161 titled Method and System for Real Time Automated Change Detection and Classification for Images hereinafter NRL . The abstract of NRL provides A computer based system and method for real time display of co registered historical and current side scan sonar imagery during a side scan sonar survey. Embodiments also include modules for detection of clutter in the current imagery identification of features extraction of snippets filtering based on predetermined size and shape parameters and determination if a current feature is the same as a previously identified contact from historical imagery. 

Mine counter measure MCM techniques have been developed to classify objects as mines or non mines using automation to detect points of interest. Human beings make final classification decisions. MCM techniques are addressed in Reference 2 below. The shape size and acoustic characteristics of a wide variety of mine types are known or at least knowable. For a given operating environment certain types of mines may be expected. Therefore MCM software has the advantage of knowing to a level of certainty what targets look like in acoustic data while rocks tires barrels and other objects represent undesirable clutter. MCM software is designed to distinguish mines from clutter objects which is a multiclass classification problem. By their nature objects may take any shape or size. Objects that are clutter for the MCM software may however be objects of interest in other situations.

Change detection may be performed at pixel level or object level. Pixel level and object level processing are addressed in Reference 3 below.

In object level processing entities such as rocks tires and barrels are first detected as contacts and then correlated with a database of known objects to detect new ones. There are a number of known techniques to identify objects. In some techniques pixels corresponding to objects are distinguished from background pixels and are logically clustered. Each cluster represents a contact. Some techniques incorporate heuristics to determine contact boundaries and characteristics to verify detection. Contacts are then compared and correlated with a list of known objects. Uncorrelated contacts represent changes. An object level change detection approach is addressed in Reference 1 below.

In contrast pixel level processing involves comparing sonar data sample by sample each sample is a pixel to look for changes and then clustering or otherwise describing these changes in a way that can indicate the presence of a new object.

Pixel level processing requires a relatively high degree of registration to perform the comparison. In other words the pixels must represent the same physical patch of ground. At centimeter resolution the allowable errors in measuring sensor pitch heading and location become extremely small. For example registering a 1 centimeter cm pixel at a 75 m range requires a heading accuracy of better than 0.1 mrad and obviously a geo location accuracy of less than 1 cm. Due to the high aspect dependency of the scattering surfaces the sensor path must be followed exactly. A few meters difference in depth or cross track positioning may compromise the data. Warping the sonar data with image processing techniques may not accurately describe areas that were not actually covered by the sensor referred to herein as inter beam holiday regions and may not sufficiently eliminate intra image distortions resulting from unknowable sensor heading and location errors. Such registration requirements may render pixel level processing unfeasible for many applications.

Issues associated with pixel level registration and potential compensation techniques are addressed in References 4 through 6 below.

Disclosed herein are methods and systems to detect changes within an area including to identify objects in sonar images of the area to compare the detected objects to a database of known objects in the area and to identify any changes within the area. Newly detected objects may be presented to a human operator in real time.

Also disclosed herein are methods and system to detect changes based on multi frequency band sonar data.

Also disclosed herein are methods and system to represent multi dimensional sonar data such as multi frequency band sonar data and corresponding position information as support vector data description SVDD statistics and to identify and characterize objects from the SVDD statistics including to characterize an object with respect to one or more invariant features which may be based on locations of points on a boundary of the object relative to other points on the boundary.

Also disclosed herein are methods and system to correlate multi dimensional characteristics of newly detected objects or contacts with multi dimensional characteristics of known objects and to optimally assign contacts to known objects.

Also disclosed herein are methods and system to manage a database of objects including to add new objects for contacts that do not correlate to existing or known objects and to manage a confidence metric associated with the objects.

In the drawings the leftmost digit s of a reference number identifies the drawing in which the reference number first appears.

Where targets of interest are unknown or undefined direct object detection may be challenging or potentially precluded. Change detection may be performed relative to a known or determinable background.

Data processing system may be configured to identify potential objects referred to herein as contacts within a survey area and to compare the contacts to known objects within the area. Known object data may be stored in a repository such as a database.

Data processing system may include an anomaly detection system to detect anomalies against a natural background such as a sea bed a contact detection and characterization system to identify and characterize contacts from the anomalies and a change detection system to correlate characterized contacts with objects in repository .

Contacts that do not correlate to known objects may represent potential new objects. Data processing system may be configured to notify an operator station in real time of detected changes such as potential new objects.

Data processing system may be configured to process multiple frequency band sonar data . For example sonar system may include a side looking multiple frequency band sonar system such as an EdgeTech 4200 dual frequency band 300 and 600 kHz side scan sonar system Reference 9 .

Sonar system and sonar data are not however limited to single or dual frequency bands. Sonar system may be configured for and sonar data may include N simultaneous frequency bands where N may be equal to or greater than 1 including greater than 2.

The simultaneous multiple frequency bands may have different corresponding sampling rates and anomaly detection system may be configured to time align the multiple frequency band sonar data . Time alignment may include re sample the multiple frequency band sonar data to at a common sample rate.

Environment may include a classification system to create new objects corresponding to contacts that do not correlate to existing or known contacts and to manage confidence metrics associated with the object. For example classification system may be configured to classify new objects as tentative objects to re classify tentative objects as confirmed objects after repeated identification of the corresponding contacts in subsequent surveys and to remove or to reclassify objects to tentative objects when corresponding contacts do not appear in subsequent surveys. Object classification system may be configured to operate subsequent to a survey which may preserve processor resources during the survey.

Anomaly detection at may include detecting data that do not appear to be background. This may include distinguishing object pixels from background pixels. Such anomalous pixels may be part of an object or spurious background returns. Anomalous data may be analyzed and processed as described below.

Anomaly detection is a useful technique to classify data when characteristics of the background are known or determinable. Of the potential billions of pixels that represent a surveyed channel a relative large majority may correspond to bottom sediment background. Because varying environmental effects along a water channel may produce relatively significant background variation it may not be practical to model the background statistically.

Anomaly detection at may be performed with a relatively large margin classification technique to classify data without statistical estimation such as a support vector data description SVDD technique. SVDD is addressed in References 7 and 8 which are incorporated herein by reference in their entireties. Exemplary SVDD techniques with respect to anomaly detection are described below with respect to of .

Where sonar data includes multi frequency band data the sonar data may provide additional data to detect objects relative to single band data. For example returns from objects may appear in multiple bands while returns from sediment scattering may appear in fewer than all bands.

The EdgeTech 4200 for example collects data from both frequency bands simultaneously but provides the data for each band at a different sample rates. For example during sea tests described below the EdgeTech 4200 was operated at a nominal 10 Hz ping rate providing a 75 m range for an assumed speed of sound of 1500 m s. The higher frequency band nominally provides a 1 cm range resolution while the lower frequency band provides a 3 cm range resolution.

As noted above sonar data is not limited to single or dual frequency bands and may include N frequency bands where N may be equal to or greater than 1 including greater than 2.

To align the data samples both bands may be re sampled. The number of samples collected during a survey and the ping interval may be utilized in the re sampling. With sonar set to provide a certain maximum range an optimum or desired number of samples collected at the highest resolution 1 cm may be determined. Then given the number of desired samples and the number of actual samples a re sampling factor may be determined. Signal re sampling may be performed with a polyphase structure. Signal re sampling with a polyphase structure is addressed in Reference 10 which is incorporated herein by reference in its entirety.

Re sampled signal amplitudes for the high frequency and low frequency bands may represent two dimensions of data for object detection. The data may exhibit spatial trends which may be taken into account. For example due to factors that may include without limitation attenuation loss spreading loss beam shape ambient noise and volume reverberation each scan line amplitude versus time return for a single ping may exhibit a logarithmic shape. is a graphic depiction of an exemplary scan line corresponding to one side of a side scan sonar survey. Relatively large sand waves which may measure several meters in length may also affect cross range dimension. Data may be normalized to remove such uninformative trends.

Physical coordinates such as in castings and northings of each sonar data sample may be calculated and used as additional feature dimensions referred to herein as third and fourth feature dimensions respectively. The physical coordinates may be calculated using a Universal Transverse Mercator UTM projection. UTM is addressed in Reference 11 which is incorporated herein by reference in its entirety.

In signals in the first 2500 samples correspond to 25 meters with a 1 cm range resolution. A first portion is relatively noisy and a second portion corresponding to approximately the first 1000 samples corresponds to the holiday region beneath the sonar sensor. Data associated with portion and may be ignored and survey paths may be aligned and or overlapped to obtain data for the corresponding areas. is a graphic depiction of exemplary inbound and outbound sensor paths and respectively.

Returning to anomaly detection at may include generating a support vector data description SVDD of the feature space construction at .

Inputs to an SVDD classifier may include a multi dimensional feature space such as described above with respect to which may include re sampled signal amplitudes of high frequency and low frequency bands and corresponding physical coordinates. Samples from the feature space may be assumed to represent background data and the SVDD may be trained to recognize these samples.

Training samples that are identified as anomalies may be removed and the SVDD may be re trained on the remaining training samples. Such an iterative training process may reduce or eliminate non background samples from the training which may result in a more accurate SVDD decision surface.

Mathematically the SVDD may describe or define training samples of a training set T in a relatively high dimensional space through a kernel function transformation and may then determine parameters of a smallest hypersphere S that can encompass the training set T which may be subject to one or more constraints. S and T may be define as 1 . . .

The hypersphere may be manifest as a relatively complex possibly disjoint decision boundary in the original four dimensional feature space. Finding the smallest hypersphere S that contains the training set T may be a constrained optimization problem which may be represented as min subject to 1 1 

In equation 1 x is a higher dimension feature space mapping. Calculation of the hypersphere may be solved through calculus of variations. Calculus of variations is addressed in References 7 and 8 which are incorporated herein by reference in their entireties.

through the selection of with 0 and 1. Typically a large number of the Lagrangian multipliers will be zero. The rest correspond to the support vectors of the training set T. The higher dimension feature space mapping x is taken as the Gaussian Radial Basis Function RBF 

Feature vectors that lie outside the hypersphere may be identified as anomalies. Substituting expressions and simplifying gives the final SVDD decision statistic for an unknown feature vector z as 

Conventional statistical detection approaches involve modeling data and estimating parameters of the model. Challenges with such approaches include determining a data model. For example where the sonar data is treated as a random process the underlying distribution of the process may not be readily discernable or definable. Another challenge with conventional statistical detection approaches is determining distribution parameters. Distribution parameters may be approximated from measured data that are binned to form estimated probability density functions. For data of more than one dimension binning may pose challenges. For example as the number of dimensions increases the likelihood of measuring samples to populate each bin may be reduced. Where the probability density functions are not accurately estimated unpredictable detection performance may be encountered. Where the sonar data random process is not stationary multiple models may be required which may further complicate the challenges above.

An SVDD approach as disclosed herein may negate such challenges by examining the data directly. An optimal decision boundary may be determined by points on or near an SVDD surface referred to herein as support vectors. With relatively little tuning an SVDD may define a relatively complex surface that envelops the background data leaving anomalies outside.

In the examples of three dimensional data are shown for illustrative purposes. Method may be implemented with data of greater and lesser dimensions.

An advantage of SVDD as disclosed herein is that once trained high variability in the background data may have substantially little or no impact on the ability of the SVDD to detect anomalies. Training involves sampling the background at numerous representative locations. SVDD is also able to handle multiple frequency bands.

Another advantage of SVDD is that because additional dimensions do not lead to sparse training sets SVDD may be applied to other types of sensors with multiple frequencies and or aspects or beams.

The placement of a SVDD decision boundary such as illustrated at represents a threshold operation to which points are subjected. Points within decision boundary are background. Points outside decision boundary are anomalies. Decision boundary may represent an optimal boundary in a mathematical sense. Costs associated with misclassification are not however necessarily equal between background and anomaly. To reduce false alerts a minimum distance or threshold beyond decision boundary may be defined beyond which a data point must lie to be an anomaly. This may be equivalent to increasing the radius of the SVDD hypersphere or decision boundary .

Thresholding at may include a hysteresis threshold. First the SVDD decision statistic may modified by 

where z is the original SVDD decision statistic and R is the SVDD hypersphere radius. The hypersphere radius may be determined by computing the SVDD statistics for a support vector that lies exactly on the hypersphere. By definition the smallest statistic value of any support vector is the radius. Equation 5 normalizes the data so that points on the hypersphere have a value of zero and all points are expressed in relation to the hypersphere size. This may be useful where the SVDD classifier is constantly retraining during real time operations and the hypersphere size may vary from one training cycle to the next.

Then all points with a value less than a threshold are set to zero and the remaining points are clustered at . If a cluster does not contain a data sample above a second higher threshold the points for that cluster are set to zero and the cluster is discarded. This two stage thresholding technique allows for detection of less obvious anomalies while preserving good false alert performance. There are many approaches to thresholding data but this approach has proven effective. Hysteresis thresholding is addressed in Reference 12 which is incorporated herein by reference in its entirety.

Clustering at may combine the individual threshold crossings which may correspond to a binary data surface in the SVDD decision space to enable detections of whole objects. An object may be represented in the sonar data by many individual samples in relatively close spatial proximity to one another. Clustering at may identify groups of samples in relatively close spatial proximity.

Clustering may include selecting a nonzero pixel and then examining neighbor pixels. A neighbor is a pixel that is simply in the row or column next to a point under consideration. Nonzero neighbor pixels may be added to the cluster. The process may repeat recursively for each nonzero neighbor until a pixel is found that has no nonzero neighbors that are not already members of the cluster. This approach works when pixels are located at fixed integer locations as represented by a matrix.

Where pixels correspond to arbitrary locations clustering at may include clustering pixels when they are within a distance r of one another. When this approach is applied to each nonzero pixel clustering of scattered sonar pixel data may be performed in Noperations where N is the number of nonzero pixels. The processing may be reduced to approximately NlogN operations. Clustering at may result in a list of clusters that are themselves lists of individual pixels.

Object detection at described below may include omitting or discarding clusters based on size such as clusters of pixels having a length and or width dimension below or outside of a threshold. This prescreening may reduce or eliminate clusters that result from spurious SVDD responses and may reduce corresponding false alerts.

At potential objects or contacts may be detected and characterized. Contacts may be detected or defined as clusters of anomalous sonar data as described above with respect to .

Contact characterizations may be subsequently compared to characterizations of known objects at similar locations such as described below with respect to . At least a portion of the characterizations may be based at least in part on perimeter or boundary information associated with contacts and objects. Accordingly characterization at may include determining perimeter or boundary information such as described below with respect to and characterizing contacts with respect to shape and size such as described below with respect to .

Contact detection at may include separating sonar data corresponding to the contacts from the seafloor background. The anomalousness of the sonar data as determined by the SVDD is a useful measure to determine set membership in part because SVDD reduces multiple data layers such as individual frequency bands aspects and beams into a single layer.

SVDD data may however be limited to representation of relatively sparse non uniform measurements of the sonar. Characterization at may thus include converting the relatively sparse non uniform measurements to a relatively regularly sampled representation of the contact perimeters. One or more of a variety of scattered data interpolation techniques such as projection onto convex sets POCS may be implemented to convert the relatively sparse non uniform measurements to a relatively regularly sampled representation of the contact perimeters. POCS is addressed in Reference 13 which is incorporated herein by reference in its entirety.

Alternatively or additionally a spline function such as a basis or B spline function may be implemented.

In contact detection and characterization at may include B spline interpolating at . B spline interpolating at may include a multilevel B spline algorithm MBA . MBA is addressed in Reference 14 which is incorporated herein by reference in its entirety.

An MBA iteratively fits a B spline surface to the scattered data to form a control lattice which can be used to estimate a surface through the scattered data at regularly spaced points. B spline interpolation may be computationally less expensive and less complex to implement relative to other techniques.

Side scan sonar data of an object may differ each time the object is sensed by the sensor. This may be due to one or more of the relatively high aspect dependency of the individual reflecting surfaces of the object variability of the medium and variation of position and orientation of the sensor relative to the object. The inconsistent sonar returns may raise challenges in change detection because visual appearance or amplitude alone may be insufficient to accurately detect changes.

Much work has been done in the image processing field to overcome affine transformations due to rotation and aspect changes as well as additive or multiplicative noise but the assumption of a consistent object appearance is fundamental to these methods. For example the method outlined in Reference 15 is widely considered state of the art in interest point detection and association. But it implicitly assumes that an object looks like the entity it is no matter how it is viewed.

Size and shape of contacts may be inferred from side scan sonar measurements with relatively minimal error. Boundary determination at may exploit these properties for object matching. As described below with respect to in a contact may be characterized with respect to size and shape based on locations of points on a surface relative to other points on the surface. Therefore affine transformations due to changes in perspective do not affect the calculations. Similarly rotation translation and scale are not factors provided the surface of the object is described within a fixed reference frame. Because only the boundary of the object is used for description the actual appearance of the object and any noise or distortion within it may be relatively inconsequential. Additionally while severe noise blurring and similar distortions may alter the apparent boundary of an object the features to be developed may be aggregates of the overall boundary. Localized changes to the boundary may impact the feature calculation only modestly.

Boundary determination at may include one or more of a variety of techniques. For example in optical image processing an active contour model also known as a snake algorithm defines an energy functional v s x s y s with arc length s as a parameter in the equation 

Erepresents the internal energy of the contour due to bending and discontinuities. Erepresents the image forces typically due to gradients. Erepresents the constraints applied to the contour. The snake algorithm iteratively changes the points along the contour to minimize the total energy in Equation 2 . Snake algorithms are addressed in Reference 16 and an expanded version of the snake algorithm is addressed in Reference 17 both of which are incorporated herein by reference in their entireties.

In an initial contour is illustrated as an ellipse that encompasses the contact or shipwreck. As the algorithm progresses through coordinates of contour are repositioned as contours through respectively to minimize energy subject to constraints and to shrink the contours. In contour substantially reflects the two dimensional shape or perimeter of the shipwreck. In this example contour was achieved in 100 iterations and contours through correspond to iterations 20 40 60 and 80 respectively.

Another approach includes convolution which may include convolving a B spline reconstructed image with a convolution kernel such as a circularly shaped convolution kernel.

A contour of a contact may be defined as a path that the center of the convolution kernel would trace when rolled around the contact. The size of the circle determines the extent to which concavities of the contact are recognized. Smaller circles fit into smaller regions. Larger circles skip over larger regions.

The contour at a particular threshold level may serve as a boundary of the object. The threshold level may be set to the highest level for which a single continuous boundary is formed. Higher threshold levels may result in disjoint boundaries. Lower threshold levels may result in inaccurate boundaries. The convolution operation is relatively tolerant of noisy peaks while providing a close fit to the actual contact or potential object.

Contact detection and characterization at may include characterizing contacts with respect to one or more of size and shape at .

Applications of six exemplary descriptors determined from the size and shape of an object are described below. Alternatively or additionally other descriptions may be used. Descriptors are addressed in Reference 18 which is incorporated herein by reference in its entirety.

Exemplary size descriptors include length and width of a contact. Size descriptors may also include height where height information is available.

To calculate descriptors contact boundary points may be projected onto two orthogonal axes in a fixed orientation and the extent of the points along each axis may be calculated. The fixed axes may correspond to a Universal Transverse Mercator UTM coordinate grid. Where the perimeter of the contact is defined by a set of points x y in the fixed reference frame the length descriptor L may be determined as MAX MIN 7 

One or more shape descriptors may be defined to characterize an overall pattern formed by the perimeter set x y .

Exemplary shape descriptors include convexity principal components compactness and circularity. Shape descriptors are addressed in Reference 19 which is incorporated herein by reference in its entirety.

Convexity may be defined as a ratio of the curve length of the convex hull of x y to the curve length of the full perimeter x y . The convex hull of a set of points may be defined as the minimal convex set containing all the points. An area may be defined as convex if for all pairs of points within the area a straight line segment between the points falls entirely within the area. A similar definition may be applied to areas in two dimensional space.

If x y is the M point subset of perimeter points that define the convex hull the perimeter of the convex hull may be defined as 

The range of values is theoretically 0 1 but values for actual shapes likely to be encountered may be towards the upper end of the range.

Convexity may be used to represent an intricacy of a contact boundary. Contacts with many concavities may have lower values of convexity. Barrels spheres tires and similar objects may have K 1. Entities that are collections of objects such as debris fields or that have irregular shapes may have smaller values. In the example of perimeter may have a convexity value of 0.97 indicating that it is mostly convex.

Principal components may be defined as a ratio of principal axes of a contact. If the perimeter of a contact x y is taken as a population of two dimensional data the principal axes may be defined as orthogonal directions along which the data are uncorrelated. Rotating the perimeter into this reference frame allows analysis of the dominant modes of the shape. The ratio of the axes describes a dominance of a primary mode. is a graphic depiction of an exemplary orientation and relative proportions of principal axes for perimeter of . In the example of the ratio is approximately 0.26 1.

If x and y are column vectors containing the coordinates of the perimeter of an object in the fixed reference frame a 2 2 covariance matrix A calculated between these vectors can be defined as 

The compactness descriptor compares the squared perimeter of the object with its area. The descriptor is referenced to a circle equal in area to the object to normalize the descriptor to the range 0 1 solely because a circle has the minimum ratio of 4 . This normalization differs from a circularity descriptor described below. If the perimeter length of the object is given by S and the area of the object is A the compactness descriptor C is 

Elongated objects will have values near 0. Round objects will have values near 1. The object in has a value of 0.62. The area of an object given N perimeter points x y is given by 

A circularity descriptor or circular variance may be determined by fitting the object perimeter to a circle in a least squares sense. The circular variance may be defined as an overall error of the fit.

Fitting data to a circular region is common in physics biology medicine archeology industry and other disciplines. Data fitting to a circular region is addressed in Reference 20 which is incorporated herein by reference in its entirety. A circular region is a natural shape for side scan sonar object analysis too because many objects appear circular. However with side scan sonar whether the perimeter of an object fits well to a circle is neither good nor bad. It is simply information.

the parameters a b and R may be determined through a nonlinear solution technique such as a Levenberg Marquardt method. Levenberg Marquardt method is addressed in References 21 and 22 which are incorporated herein by reference in their entireties.

which has the effect of limiting it to the range 0 1 . This descriptor has a value of 1 for a perfect circle and a smaller value for other shapes. The descriptor for is 0.0038.

The exemplary descriptors described above may be used to characterize contacts or objects from side scan sonar data where the size location orientation and appearance of the objects may vary between data from different surveys. The descriptors are relatively invariant to these effects because they characterize the locations of points on the object surface relative to other points on the surface. Localized changes to the surface due to detection errors may only modestly impact the descriptor calculation.

Once calculation of the descriptors is complete and objects in a particular geographical area have been detected and characterized at two different times the automated detection problem is reduced to change detection. The goal now is to recognize new objects in the most recent observation.

Objects previously detected in an area may be cataloged in a database that includes the current and historical geographical locations and descriptors. To account for movement of objects due to natural forces historical position information may be retained and objects may be tracked over time. Current object locations can then be predicted for better correlation. When changes are to be detected for a specified area the database is queried for all known objects within the area. The query parameters may include geographical coordinates. The resulting list may be used to perform a many to many correlation such as described below with respect to .

Change detection at may include calculating a Euclidean distance at or other similarity dissimilarity measurement between contacts and known objects.

Euclidean distance may be derived from physical locations of contacts and objects and corresponding shape and size descriptors. Each Universal Transverse Mercator coordinate and the exemplary six descriptors may be treated as separate dimensions resulting in an eight dimensional distance calculation. If the eight element vector corresponding to a contact is u and the eight element vector corresponding to a known object is V then the scalar distance between the contact and the object is 

A contact may correlate with an object when the distance is less than a maximum tolerable distance . When a contact is physically distant from an object this tolerance may be exceeded and there is no correlation even if only one object and one contact are in the greater vicinity. represents a physical correlation window. In situations where multiple contacts and or objects are within distance of each other physically the differences in shape and size dimensions may become distinguishing factors. In other words shape and size characteristics may be used as effective tie breakers when physical distance is ambiguous.

Change detection at may include an optimal assignment at which may include a many to many correlation based on the distance metric calculated between each contact and each object.

Many to many correlation of contacts to objects may be a relatively complex problem. It may however be viewed as a classic worker task assignment problem with a scalar cost metric. In a worker task problem specific tasks may be assigned to specific workers based on corresponding abilities to perform the tasks which may minimize the overall cost to complete the tasks.

Optimal assignment at may include assigning contacts to objects so as to minimize a total N dimensional distance. In cases where multiple contacts could be assigned to multiple objects the formulation of the descriptor vector and the calculation of distance may dictate that a combination of physical distance shape and size determines the assignment.

Optimal assignment was published over 50 years ago by Kuhn References 23 and 24 in what is now known as the Hungarian Algorithm. The original algorithm was modified by Munkres Reference 25 and the current method is now often called the Kuhn Munkres Algorithm or simply the Munkres Algorithm. The method was further modified by Burgeois and Lassalle Reference 26 for application to rectangular matrices for example when the number of detections and pre existing tracks are different . Optimal assignment at may include one or more of the above including the Burgeois and Lassalle adaptation. References 23 24 25 and 26 are incorporated herein by reference in their entireties.

Optimal assignment at may be implemented in accordance with Reference 27 which is incorporated herein by reference in its entirety. The following description is taken almost directly from this reference. The problem begins with a P Q matrix where P contacts represent rows Q objects represent columns and each element of the matrix represents the distance between the corresponding contact and object. The algorithm consists of the following steps 

By the end of the process there will be k starred zeros which represent the contact object correlations. Any contact that remains uncorrelated represents a potential new object. These are detected changes and mark the output of the automation algorithm. An operator may be alerted to these contacts and may determine whether they represent actual objects or are false alerts. Decisions of the operator may be incorporated by the algorithm and used for object management such as described below.

Change detection information obtained from a new survey may be incorporated within repository of known objects which may be performed off line or subsequent to a survey.

Exemplary off line processing of change detection information is described below with reference to method in .

At an indication of detected contacts and corresponding contact object correlations associated with a new survey are received. The indications may be generated in accordance with change detection at in .

During real time operation a log may be maintained with each detected contact and all contact object correlations. The log may be received at .

At one or more actions are taken in response to results of the correlations. Correlation results may include one or more of 

Case 1 may correspond to a situation where a previously observed or known object is observed during a new survey. At based on new observation information new predicted positions of the objects may be calculated and stored.

Objects may be classified as tentative objects or confirmed objects. Classification may be based at least in part on a prior number of prior surveys in which the object was detected. At where the object is currently identified as a tentative object a corresponding confidence or track metric may be increased at . At if the track metric exceeds a confirmation threshold the object may be re classified as a confirmed object at .

Case 2 may correspond to a situation where a known object is not detected in a subsequent survey. At the object may be marked as unseen and the track metric of the object may be decreased. At when the track metric of the object falls below a drop threshold at the object may be removed from repository in .

Case 3 may correspond to a new or previously undetected object. At a new object may be configured in repository to represent the uncorrelated contact. A corresponding track metric may be initialized to identify the new object as a tentative object. Subsequent observations of the contact may improve the track metric and may lead to promotion of the corresponding object to a confirmed object.

Case 3 may be invoked to initialize repository and may be invoked to re initialize repository or a portion thereof in response to an event such as a severe weather event that may substantially disturb a corresponding survey area.

Case 3 contacts may be presented to an operator in real time. Where the operator validates a case 3 contact the contact may be subsequently added to repository as a confirmed object. Where the operator invalidates a case 3 contact the contact may be added to repository as a potentially invalid or false object. A subsequently detected contact that correlates to the object may be automatically identified as a false object which may preclude presentation of the contact to the operator.

A first survey of an area was performed at sea in December 2006. Block was not present in the area during the first survey. Block was subsequently placed in the survey area.

A second survey was conducted in mid August 2007 subsequent to the placement of block in the area. A third survey was conducted in late August 2007 with block present in the area.

Data from the December 2006 survey represents baseline data to which data from the August 2007 surveys may be compared.

Although segments and differ from one another with respect to aspect angle to any particular point the acoustic data show little significant variation.

In the experimental results reported positions of block in the two August 2007 passes differ by approximately 2.07 meters due to errors in the sensor position measurements.

Geo registered acoustic data and were processed as described in accordance with method as described below.

Boundaries and are similar to one another. Descriptor vectors calculated for boundaries and including length L width W and the x y coordinates are given in Table 1 below. For illustration purposes the coordinates of the first contact are taken as the origin. Excluding the coordinates and treating the other six descriptors as elements of a vector for each segment allows an angle of separation to be calculated by 

This angle describes the similarity of two boundaries in shape and size. Identical boundaries will have an angle of zero.

Because the detected and cataloged object from the first segment is the only object in the vicinity for the second segment the correlation is obvious. From Equation 21 the total eight dimensional separation is 2.07 units and the angular separation calculated from Equation 22 is 4.2 . Thus even if there were more database objects in the area the correlation would be correct for any objects that were at least 2.07 meter away from the concrete block. For objects closer than 2.07 m the correlation would still be correct provided the angular separation between the first segment detection and the confusable object is more than 4.2 .

Data quality may be affected by one or more factors such as consistency of sensor deployment and accuracy of sensor localization or data registration. For example where the acoustic background is relatively unchanged between surveys false detections may be reduced. More frequent surveys may minimize effects of naturally occurring changes. Other factors may include 

One or more features disclosed herein may be implemented in hardware software firmware and combinations thereof including discrete and integrated circuit logic application specific integrated circuit ASIC logic and microcontrollers and may be implemented as part of a domain specific integrated circuit package or a combination of integrated circuit packages. The term software as used herein refers to a computer program product including a computer readable medium having computer program logic stored therein to cause a computer system to perform one or more features and or combinations of features disclosed herein.

Computer system includes memory storage including a computer readable medium having computer program product logic or instructions stored thereon to cause processor to perform one or more functions in response thereto.

Memory storage further includes data to be used by processor in executing instructions and or generated by processor in response to execution of instructions .

In the example of logic includes data processing logic which may include logic to cause processor to implement method or portions thereof.

Data processing logic may include anomaly detection logic to cause processor to generate cluster data from multi frequency band sonar data such as described in one or more examples above. Anomaly detection logic may include one or more of feature space logic SVDD logic threshold logic and cluster logic to cause processor to generate one or more of time aligned sonar data from sonar data to generate SVDD data from time aligned data and to generate cluster data from SVDD data such as described above with respect to .

Data processing logic may include contact detection and characterization logic to cause processor to identify and characterize contacts from cluster data . Contact detection and characterization logic may include one or more of B spline interpolation logic boundary determination logic and characterization logic to cause processor to determine boundary data from cluster data and to generate contact characterization data from boundary data such as described above with respect to .

Data processing logic may include change detection logic to cause processor to compare contact characterization data including corresponding position information with characterization and position data of known objects to correlate contacts with known objects based on the comparisons and to generate optimal assignments such as described above with respect to . Change detection logic may include Euclidean distance logic to calculate Euclidean distances between contacts and objects based on multi dimensional characterization data and may include optimal assignment logic to correlated contacts with objects to minimize an overall distance metric.

Change detection logic may include notification logic to notify an operator in real time of contacts that do not correlate to known objects.

Logic may further includes classification logic which may include logic to cause processor to implement method or portions thereof. Classification logic may include logic to cause processor to manage known objects including to add new contacts to delete old objects and to update track metrics associated with objects such as described above with respect to .

Execution of logic or portions thereof may be distributed amongst a plurality of computer systems and or processor cores such as to optimize processing resources. For example computations may include matrix based operations that may be distributed across multiple processors or processor cores which may be configured in a parallel processing architecture.

Although actual processor utilization is data dependent given the data rates of the exemplary EdgeTech 4200 side scan sonar eight processors such as Intel Pentium 4 3.6 GHz processors may be sufficient for real time operation. Processor may thus include for example dual quad cores.

Computer system may include a communications infrastructure to communicate amongst components of computer system .

Computer system may include an input output controller to communicate with one or more of sonar repository operator station repository and other systems over one or more communication channels or links which may include a network communication channel and which may include an Internet communication link.

Methods and systems are disclosed herein with the aid of functional building blocks illustrating the functions features and relationships thereof. At least some of the boundaries of these functional building blocks have been arbitrarily defined herein for the convenience of the description. Alternate boundaries may be defined so long as the specified functions and relationships thereof are appropriately performed.

One skilled in the art will recognize that these functional building blocks can be implemented by discrete components application specific integrated circuits processors executing appropriate software and combinations thereof.

While various embodiments are disclosed herein it should be understood that they have been presented by way of example only and not limitation. It will be apparent to persons skilled in the relevant art that various changes in form and detail may be made therein without departing from the spirit and scope of the methods and systems disclosed herein. Thus the breadth and scope of the claims should not be limited by any of the exemplary embodiments disclosed herein.


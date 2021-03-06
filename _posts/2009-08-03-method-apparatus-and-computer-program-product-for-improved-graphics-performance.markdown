---

title: Method, apparatus, and computer program product for improved graphics performance
abstract: This relates to a generation of digitally represented graphics. A first representation of a group of vertices is received. A second representation of said group of vertices is determined based on said first representation. A first set of instructions is executed on said second representation of said group of vertices for providing a third representation of said group of vertices, said first set of instructions being associated with vertex position determination. The third representation of said group of vertices is subjected to a culling process.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08654122&OS=08654122&RS=08654122
owner: Intel Corporation
number: 08654122
owner_city: Santa Clara
owner_country: US
publication_date: 20090803
---
The present invention relates to digitally represented graphics and more particularly to a method an apparatus and a computer program product for improving the performance of generating digitally represented graphics.

Digitally represented graphics such as computer graphics is continuously improving in performance. In the 1980 s and 1990 s display adapters for computers and game consoles appeared with graphics accelerators offloading the Central Processing Unit CPU in graphics generation. Initially the display adapters offered acceleration of 2D graphics but eventually these also included support for accelerated 3D graphics. Modern display adapters use a processing unit named a graphics processing unit GPU .

Due to the complexity of 3D graphics GPUs of today use a significant amount of their processing power to perform calculations related to 3D graphics.

A continuous disadvantage with display adapters is performance. There are new applications and games requiring maintained frame rates rendered screen images per second with higher scene complexities higher geometry detail higher resolutions and higher image quality resulting in requirements that each screen image should be rendered in a short a time as possible. In other words it is often important to increase performance.

One known way to increase performance is to increase the processing power of the GPUs by enabling higher clock speeds pipelining or exploiting parallel computations. However this often results in a higher power consumption and more generated heat. For battery operated devices a higher power consumption leads to a reduced battery life. Power consumption and heat are major constraint and bottlenecks for mobile devices and desktop display adapters. Moreover there are limits to the clock speeds of each GPU.

Embodiments of the present invention will now be described more fully hereinafter with reference to the accompanying drawings in which certain embodiments of the invention are shown. This invention may however be embodied in many different forms and should not be construed as limited to the embodiments set forth herein rather these embodiments are provided by way of example so that this disclosure will be thorough and complete and will fully convey the scope of the invention to those skilled in the art. Like numbers refer to like elements throughout. is a block diagram illustrating how different entities in a conventional display adapter known to a person skilled in the art interact. A display adapter according to prior art may comprise a vertex shader a triangle traversal unit and a fragment shader . The entities of the display adapter according to prior art are well known to persons skilled in the art.

The input to the vertex shader is a vertex. In computer graphics a vertex comprises data associated with a location in space. For example a vertex may be all data associated with a corner of a primitive. The vertices are associated riot only with three spatial coordinates but also with other graphical information necessary to render objects correctly such as colours reflectance properties textures and surface normals. Each vertex may also be associated with other attributes such as normals and texture coordinates.

A connected set of vertices can be used to define a primitive. A primitive may for example be a triangle quadrilateral polygon or other geometric form or alternatively a primitive may for example be a surface or a point in space. A primitive that is represented as a triangle has for example three vertices and a quadrilateral has four vertices.

The vertex shader comprises a set of instructions that are executed for each vertex. The set of instructions may for example comprise a simple matrix transform a projective transform a blend of matrix multiplications textured and procedural displacement.

The triangle traversal unit is responsible for setting up polygons as instructed by a connected controller. Although any polygon can be used triangles are commonly used. For each polygon the triangle traversal unit divides the polygon to be rendered into one or more tiles where each tile is at least partly overlapped by the polygon. In general a tile is a two dimensional rectangle comprising a number of fragments. Each of these fragments correspond to a pixel and comprise all data required to render the pixel and to test whether the pixel should be rendered on the screen. A common size of a tile is 8 by 8 fragments although any tile size is possible.

Another important task of the triangle traversal unit is to find the fragments that are inside the geometric primitive e.g. triangle being rendered. This can be done using a variety of techniques the techniques being known to a person skilled in the art.

The fragment shader executes a fragment shader program for each fragment passed to this unit. Each of these fragments correspond to a pixel and comprise data required to render the pixel and to test whether the pixel should be rendered on the screen. The fragment data may include at least one from the group of raster position depth colour texture coordinates stencil or alpha used for blending . For every pixel there may exist a plurality of fragment samples.

The fragments are further processed in order to for example combine a previously evaluated colour with textures as well as to add effects such as fog as well as to when possible identify fragments that do not need to be rendered i.e. fragment culling.

The fragment shader may further perform depth testing alpha testing and blending before the fragments are written to target buffers.

Different embodiments of an apparatus adapted to generate digitally represented graphics according to the invention will be described below with reference to . The apparatus comprises circuitry for improving performance of generation of digitally represented graphics. Said apparatus may be embodied as a display adapter and will for ease of understanding hereinafter be referred to as a display adapter.

The input to the vertex culling unit is a first representation of a group of vertices. A first representation of a group of vertices is herein to be interpreted as the vertices themselves.

In the vertex culling unit culling is performed on groups of vertices and on representations of vertices. The output from the vertex culling unit may be that the group of vertices is to be discarded.

The display adapter can further comprise a vertex probing unit see . The vertex probing unit is arranged to check if at least one vertex of the group of vertices can be culled. The at least one vertex can be the first last and or middle vertex in the group of vertices. Alternatively it can be randomly selected from the group of vertices. The vertex probing unit may use a vertex shader according to prior art to transform the vertex. The vertex probing unit then performs for example view frustum culling and checks if the at least one vertex is inside the view frustum and if it is it cannot be culled. It is however to be noted that other culling techniques known to a person skilled in the art could be used as well.

If the at least one vertex of the group of vertices cannot be culled it implies that the entire group of vertices cannot be culled and then it is better not to perform the culling in the vertex culling unit on the entire group of vertices since this culling is capacity demanding.

The vertex culling unit the input to the vertex culling unit and the output from the display adapter have been previously described in connection with

The vertex culling unit the input to the vertex culling unit and the output from the display adapter have been previously described in connection with

In one embodiment the display adapter of can also comprise a vertex probing unit which has been previously described in connection with

In yet another embodiment see the display adapter comprises a vertex culling unit a vertex shader a triangle traversal unit a fragment culling unit and a fragment shader . The entities and may be of the same or similar type as those described above with reference to .

The vertex culling unit the input to the vertex culling unit and the output from the display adapter have been previously described in connection with

In one embodiment the display adapter of can also comprise a vertex probing unit which has been previously described in connection with

In the fragment culling unit culling is performed on tiles according to a replaceable culling program also known as a replaceable culling module. The details of this culling program and the effects are explained in more detail in the International patent application PCT SE2008 000055 WO 20081091198 published Jul. 31 2008 the content of which is hereby incorporated by reference.

The embodiment of can also comprise a fragment probing unit . The fragment probing unit is arranged to check if at least one pixel from a tile can be culled. The at least one pixel can for example be the centre pixel of the tile or the four corners of the tile. If the at least one pixel of the tile cannot be culled it implies that the tile cannot be culled and then it is better not to perform the culling in the fragment culling unit since the culling may be capacity demanding.

In yet another embodiment see the display adapter comprises a base primitive culling unit a vertex culling unit a vertex shader a triangle traversal unit and a fragment shader . The entities and may be of the same or similar type as those described above with reference to .

The vertex culling unit and the output from the display adapter have been previously described in connection with . The input to the base primitive culling unit is a base primitive. A geometric primitive in the field of computer graphics is usually interpreted as atomic geometric objects that the system can handle for example draw or store. Atomic geometric objects may be interpreted as geometric objects that cannot be divided into smaller objects. All other graphics elements are built up from these primitives.

In one embodiment the display adapter of can also comprise a vertex probing unit which has been previously described in connection with

In the base primitive culling unit culling is performed on base primitives according to a culling program. The details of this culling program and the effects are explained in more detail in the Swedish Patent Application No. 0800165 3 included as Appendix A the content of which is hereby incorporated by reference.

The embodiment of can also comprise a base primitive probing unit . The base primitive probing unit is arranged to check if at least one vertex of a base primitive can be culled. At least one vertex from the base primitive is selected. The at least one vertex can for example be the vertices of the base primitive or the centre of the base primitive. If the at least one vertex of the base primitive cannot be culled it implies that the base primitive cannot be culled and then it is better not to perform the base primitive culling in the base primitive culling unit since base primitive culling is capacity demanding.

In yet another embodiment not shown in the figures the display adapter can comprise a base primitive probing unit a base primitive culling unit a vertex probing unit a vertex culling unit a vertex shader a triangle traversal unit a fragment probing unit a fragment culling unit and a fragment shader .

In step a first representation of a group of vertices is received. The received group of vertices may comprise vertices from at least two primitives.

The vertices to be input into the vertex shader are gathered into groups using so called draw calls. A draw call comprises vertices and information about how the vertices are connected to create primitives for example triangles.

The vertices in a draw call share a common rendering state which implies that they are associated with the same vertex shader and also with the same geometry shader pixel shader and also other types of shaders. A rendering state describes how a particular type of object is rendered including its material properties associated shaders textures transform matrices lights etc. A rendering state could for example be used for rendering all primitives of a part of wood a part of a man the stem of a flower. All vertices in the same draw call can be used to render objects with the same material appearance.

Usually many draw calls are needed in order to render an entire image. Draw calls are used because it is more efficient to render a relatively large set of primitives with the same states and shaders than to render one primitive at a time and having to switch shader program for each primitive. Another advantage with using draw calls is that overhead is avoided in the Application Programming Interface API and in the graphics hardware architecture.

In step a second representation of said group of vertices is determined based on said first group of vertices. The second representation of said group of vertices can be computed using bounded arithmetic according to the following 

A three dimensional model comprises k vertices p i 0 k 1 . The bounds of the x coordinates can for example be computed as tilde over p min p max p i.e. the minimum and maximum of all x coordinates of the vertices p i 0 k 1 are computed. This results in an interval tilde over p . Such an interval can be computed for all other components of p and for all other varying parameters as well. It is to be noted that other types of computations can be applied instead in order to compute these bounds. In the example above interval arithmetic is used. Affine arithmetic or Taylor arithmetic are other types of bounded arithmetic that could be used instead.

In step a first set of instructions is executed on said second representation of said group of vertices for providing a third representation of said group of vertices. When executing the first set of instructions bounded arithmetic can be used. The bounded arithmetic can for example be Taylor arithmetic interval arithmetic or affine arithmetic.

In one embodiment one or more polynomials are fitted to the attributes of the group of vertices and Taylor models are constructed wherein the polynomial part comprises the coefficients of the fitted polynomials and the remainder term is adjusted so that the Taylor model includes all vertices in the group. Such an approach may give sharper bounds than when using interval arithmetic.

In step said third representation of said group of vertices is subject to a culling process. Culling is performed in order to avoid drawing objects or parts of objects that are not seen.

The groups of vertices received in step can be gathered in different ways. One way is to use the entire draw call which implies that the first representation of the group of vertices comprises all vertices in the draw call.

Another way is to gather the vertices of m primitives where m is a constant. When using this alternative the first representation of the group of vertices can span more than one draw call.

Another way is to gather the vertices according to step see if the number of vertices in said group of vertices exceeds a threshold value divide said group of vertices into at least two subgroups wherein said at least two subgroups comprise vertices that are associated with the same set of instructions associated with vertex position determination. This way of gathering vertices is a combination of the two previously described ways. Using this way a group may not span across more than one draw call and the size of the group may not be bigger than m.

Another way to gather the vertices comprises computing intervals enclosing for example the positions of the vertices. The intervals can be computed for other parameters as well such as for example colour. Vertices are added to the group until the intervals exceed a predetermined threshold.

In one embodiment step can comprise that the second representation of the group of vertices can be computed and then stored in a memory step The next time the second representation of the group of vertices is needed it can be retrieved from the memory. This is capacity efficient since the computation does not have to be performed for every group of vertices. This solution is possible as long as the groups of vertices that are input are associated with the same set of instructions associated with vertex position determination and with the same vertex attributes. Vertex attributes can for example be vertex positions normals texture coordinates etc.

In one embodiment step can comprise that the second representation of the group of vertices can be retrieved from a memory step

In one embodiment the first set of instructions can be derived from a second set of instructions associated with vertex position determination step . The second set of instructions associated with vertex position determination is herein to be interpreted as the instructions in a conventional vertex shader of prior art.

The set of instructions is then analysed and all instructions that are used to compute the vertex position are isolated. The instructions are redefined into operating on bounded arithmetic for example Taylor arithmetic interval arithmetic affine arithmetic or another suitable arithmetic known to a person skilled in the art.

Assume that a vertex in homogeneous coordinates is denoted P p p p p where p 1 usually and is the transpose operator i.e. column vectors are used. In the simplest form a vertex shader program is a function that operates on a vertex p and computes a new position P. More generally the vertex shader program is a function that operates on a vertex p and on a set of varying parameters t i 0 n 1 see equation 1 . equation 1 

To simplify notation all the tparameters are put into a long vector t. The parameters can for example be time texture coordinates normal vectors textures and more. The parameter M represents a collection of constant parameters such as matrices physical constants and so on.

The vertex shader program may have many other outputs besides P and therefore more inputs as well. In the following it is assumed that the arguments parameters to f are used in the computation of P.

When deriving the first set of instructions associated with vertex position determination the vertex shader is reformulated so that the input is said second representation for example interval bounds for the attributes of the group of vertices and the output is bounds for the vertex positions see equation 2 . equation 2 

A brief description of Taylor models follows in order to facilitate the understanding of the following steps.

Intervals are used in Taylor models and the following notation is used for an interval equation 3 Given an n 1 times differentiable function u where u u u the Taylor model of is composed of a Taylor polynomial T and an interval remainder term circumflex over r . An nth order Taylor model here denoted tilde over over the domain u u u is then 

In one embodiment the second representation of the group of vertices can be interval bounds for the vertex attributes for example position and or normal bounds. The first set of instructions may be executed using bounded arithmetic. In this embodiment the third representation is a bounding volume. In one embodiment the bounding volume may be a bounding box. The third representation is for example determined by computing the minimum and maximum values for every vertex attribute.

In one embodiment a bounding volume enclosing said third representation of said group of vertices is determined and said bounding volume is subject to a culling process step

A bounding volume for a set of objects is a closed volume that completely comprises the union of the objects in the set. Bounding volumes may be of various shapes for example boxes such as cuboids or rectangles spheres cylinders polytopes and convex hulls.

The inventive bounding volume may be a tight bounding volume. The bounding volume being tight implies that the area or volume of the bounding volume is as small as possible but still completely enclosing said third representation of said group of vertices.

In one embodiment the second representation of group of vertices are Taylor models of the vertex attributes. The first set of instructions are executed using Taylor arithmetic. The third representation of a group of vertices may be bounds that are computed from the second representation using the first set of instructions. These bounds may be computed for example according to what is disclosed in Interval Approximation of Higher Order to the Ranges of Functions Qun Lin and J. G. Rokne Computers Math. Applic. vol 31 no. 7 pp. 101 109 1996. In one embodiment a bounding volume enclosing said third representation of said group of vertices is determined and said bounding volume is subject to a culling process.

In another embodiment the first representation of the group of vertices can describe a parameterized surface for example an already tessellated surface that is parameterized by two coordinates for example u v . In another embodiment one or more polynomial models have been fitted to the attributes of the group of vertices.

In one embodiment the third representation may be a Taylor model and can be a polynomial approximation of the vertex position attribute. More specifically it may be positional bounds tilde over p u v tilde over p tilde over p tilde over p tilde over p that is four Taylor models. For a single component for example x this can be expressed in the power basis as follows the remainder term circumflex over r has been omitted for clarity 

In one embodiment said third representation of said group of vertices may be normal bounds. For a parameterized surface the unnormalized normal n can be computed as 

One way of determining the bounding volume may be by computing the derivatives of the Taylor polynomials and thus finding the minimum and maximum of the third representation.

Another way to determine the bounding volume may be according to the following. The Taylor polynomials are converted into Bernstein form. Due to the fact that the convex hull property of the Bernstein basis guarantees that the actual surface or curve of the polynomial lies inside the convex hull of the control points obtained in the Bernstein basis the bounding volume is computed by finding the minimum and maximum control point value in each dimension. Transforming equation 5 into Bernstein basis gives 

To compute a bounding box simply the minimum and the maximum value over all pfor each dimension x y z and w are computed. This gives a bounding box circumflex over b circumflex over b circumflex over b circumflex over b circumflex over b where each element is an interval for example circumflex over b .

In this approach the positional bounds normal bounds and bounding volume derived above are used for applying different culling techniques on the groups of vertices.

In one embodiment view frustum culling is performed using said positional bound or said bounding volume step

In one embodiment occlusion culling is performed using said positional bound or said bounding volume step

In one embodiment a third set of instructions is derived from said second set of instructions and said third set of instructions is executed for providing a normal bound step

In one embodiment back face culling is performed using at least one from the group of said normal bound said positional bound and said bounding volume step

In one embodiment at least one of the steps and is performed. The steps do not have to be performed in the exact order disclosed.

The culling techniques disclosed below are not be construed as limiting but they are provided by way of example. A person skilled in the art would realise that back face culling occlusion culling and view frustum culling may be performed using various different techniques than the ones described below.

View frustum culling is a culling technique based on the fact that only objects that will be visible that is that are located inside the current view frustum are to be drawn. The view frustum may be defined as the region of space in the modelled world that may appear on the screen. Drawing objects outside the frustum would be a waste of time and resources since they are not visible anyway. If an object is entirely outside the view frustum it cannot be visible and can be discarded.

In one embodiment the positional bounds of the bounding volume are tested against the planes of the view frustum. Since the bounding volume circumflex over b is in homogeneous clip space the test may be performed in clip space. A standard optimization for plane box tests may be used where only a single corner of the bounding volume the bounding volume being a bounding box is used to evaluate the plane equation. Each plane test then amounts to an addition and a comparison. For example testing if the volume is outside the left plane is performed using 

Back face culling discards objects that are facing away from the viewer that is the all normal vectors of the object are directed away from the viewer. These objects will not be visible and there is hence no need to draw them.

where n u v is the normal vector at u v . If c 0 then p u v is back facing for that particular value of u v . As such this formula can also be used to cull for example a triangle or a group of triangles such as triangles described by a group of vertices. The Taylor model of the dot product see equations 7 and 10 is computed tilde over c tilde over p u v u v . To be able to back face cull the following must hold over the entire triangle domain tilde over c 0. The lower bound on tilde over c is conservatively estimated again using the convex hull property of the Bernstein form. This gives an interval tilde over c and the triangle or group of triangles can be culled if 0.

In another embodiment interval bounds are computed for the normals. for checking if the back face condition is fulfilled.

The testing may also be performed using the positional bounds tilde over p u v tilde over p tilde over p tilde over p tilde over p or alternatively the bounding volume.

Occlusion culling implies that objects that are occluded are discarded. In the following occlusion culling is described for a bounding box but a person skilled in the art would realise that it is possible to perform occlusion culling on other types of bounding volumes as well.

The occlusion culling technique is very similar to hierarchical depth buffering except that only a single extra level is used 8 8 pixel tiles in the depth buffer. The maximum depth value Z is stored in each tile. This is a standard technique in GPUs used when rasterizing triangles. The clip space bounding box b is projected and all tiles overlapping this axis aligned box are visited. At each tile the classic occlusion culling test is performed Z Z which indicates that the box is occluded at the current tile if the comparison is fulfilled. The minimum depth of the box Z is obtained from the clip space bounding box and the maximum depth of the tile Z from the hierarchical depth buffer which already exists in a contemporary GPU . Note that the testing can be terminated as soon as a tile is found to be non occluded and that it is straightforward to add more levels to the hierarchical depth buffer. The occlusion culling test can be seen as a very inexpensive pre rasterization of the bounding box of the group of primitives to be rendered. Since it operates on a tile basis it is less expensive than an occlusion query.

In another embodiment the testing may also be performed using the positional bounds tilde over p u v tilde over p tilde over p tilde over p tilde over p .

In one embodiment the culling process is replaceable. This implies that the vertex culling unit may be supplied with a user defined culling process.

At least one vertex is selected from the group of vertices step . A set of instructions associated with vertex position determination are executed on a first representation of said at least one vertex for providing a second representation of said at least one vertex step . The second representation of said at least one vertex is subject to a culling process step wherein an outcome of said culling process comprises one of a decision to discard said at least one vertex and a decision not to discard said at least one vertex. In case the outcome of said culling process comprises a decision to discard said at least one vertex the steps are performed. The steps described in connection with can be performed in the apparatus of the invention or embodiments of the invention.

It is to be noted that although a general purpose computer is described above to embody various embodiments of the invention the invention can equally well be embodied in any environment where digital graphics and in particular 3D graphics is utilized e.g. game consoles mobile phones MP3 players etc.

The invention may furthermore be embodied in a much more general purpose architecture. The architecture may for example comprise many small processor cores that can execute any type of program. This implies a kind of a software GPU in contrast to more hardware centric GPU s.

The invention has mainly been described above with reference to a few embodiments. However as is readily appreciated by a person skilled in the art other embodiments than the ones disclosed above are equally possible within the scope of the invention as defined by the appended patent claims.


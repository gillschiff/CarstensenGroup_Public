**Human-Informed Topology Optimization 2.0 (HiTop 2.0)**

HiTop is a human in the loop design optimization code first published in the paper "Human Informed Topology Optimization: Interactive Application of Feature Size Controls" (Ha, D. and Carstensen, J.V., 2023, Structural and Multidisciplinary Optimization 66:59. DOI 10.1007/s00158-023-03512-0).

HiTop 2.0 builds upon the original version of HiTop in the recent paper:

Gillian Schiffer, Dat Quoc Ha & Josephine V. Carstensen (2023) HiTop 2.0: combining topology optimisation with multiple feature size controls and human preferences, Virtual and Physical Prototyping, 18:1, DOI: 10.1080/17452759.2023.2268603.

Different from the original HiTop, HiTop 2.0 implements a GUI that allows for a flexible design problem formulation. Additionally, the user can make 1 or 2 changes to the minimum solid, minimum void, maximum solid, and/or passive regions of interest in the design.

**File Familiarization:**

To start, users should download the ```\HiTop2_0``` folder. Enter the folder and you will find three files.

1. Parameters.m – this is where the user specifies the parameters below. The user will also find the authors' general guidelines on what range for the parameters they have found to work best.

| ```Nelx``` | Number of elements in the x-direction | ```Nely``` | Number of elements in the y-direction |
| --- | --- | --- | --- |
| ```Volfrac``` | Volume fraction for optimization problem | ```rminS``` | Radius of minimum solid feature size |
| ```rminV``` | Radius of minimum void feature size | ```betaMMA``` | beta value for the Heavisides projection |
| ```betaHP``` | Same as betaMMA | ```Penal``` | Penalization factor for the SIMP method |

1. ```hiTopDriver.m``` – this is the driver file to run the HiTop 2.0 program.
2. ```\addpath``` folder – this folder contains the supporting MATLAB scripts and MMA folder

**How it works (with L-Bracket example):**

1. Enter the appropriate variables for your design problem in the ```parameters.m``` file
2. Run the ```HiTopDriver.m``` MATLAB script
3. Highlight location of force
* The authors recommend zooming into the mesh to ensure accurate selection.
* For best results, only select \<10 nodes and ensure the node locations are fully enclosed by your drawn rectangle Region of Interest (ROI)

|<img width="400" alt="image" src="https://github.com/gillschiff/CarstensenGroup_Public/assets/142328197/2b0c585a-965b-4111-962e-911ad41e4b0c">|<img width="400" alt="image" src="https://github.com/gillschiff/CarstensenGroup_Public/assets/142328197/dd7cba17-8f01-4bc5-b829-59df0660a777">|
| --- | --- |
| Proper selection of 8 nodes for the L-Bracket Problem | Too many nodes selected for load |
* Double click the ROIs
4. Specify the direction of the negative force with 1 = x, 2 = y, 3 = x and y
* For L-Bracket, enter 2
* Assumed positive x and y directions below
* <img width="100" alt="image" src="https://github.com/gillschiff/CarstensenGroup_Public/assets/142328197/ab70c93d-b0b9-4fb4-85da-994622c9b85d">
5. Enter whether you are going to emplace 1 or 2 boundary conditions
* For L-Bracket enter 1
6. Enter whether you want to manually draw (1) or automatically pick an edge (2) of the design domain for your boundary condition
* For L-Bracket enter 1
7. Highlight the location of the boundary condition
* Ensure your ROI only encloses the desired nodes

|<img width="300" alt="image" src="https://github.com/gillschiff/CarstensenGroup_Public/assets/142328197/dfbdb42b-274d-49c0-8bc9-adbc17771b25">|<img width="400" alt="image" src="https://github.com/gillschiff/CarstensenGroup_Public/assets/142328197/2dbfeefa-4475-4d07-9ab2-8a5b9c4cc096">|<img width="400" alt="image" src="https://github.com/gillschiff/CarstensenGroup_Public/assets/142328197/289bbeeb-2323-4007-bd4c-114e763f11b6">|
| --- | --- | --- |
|Proper selection of single line of nodes on upper edge of domain |Too many nodes selected| No nodes are selected|

* Double click the ROI
8. Specify the direction of the translation restriction with 1 = x, 2 = y, 3 = x and y
* For L-Bracket, enter 3
9. Enter whether you'd like to specify a solid (1), void (0), or no (0) passive region in the design problem
* For L-Bracket enter 0
10. Draw the passive region
* The authors find that drawing the passive region zoomed out, then zooming in to refine is a successful method to specify the passive ROI
* <img width="300" alt="image" src="https://github.com/gillschiff/CarstensenGroup_Public/assets/142328197/f65178b1-fde1-4305-9b25-d33452403aa3">
* Next, zoom into the areas of the passive ROI that may overlap with force or boundary condition ROIs

|<img width="300" alt="image" src="https://github.com/gillschiff/CarstensenGroup_Public/assets/142328197/684f1219-907f-43ce-bea5-003c8bb76357">| <img width="400" alt="image" src="https://github.com/gillschiff/CarstensenGroup_Public/assets/142328197/9487b23b-5880-41f8-97c0-9e2c5beafbc5">| <img width="400" alt="image" src="https://github.com/gillschiff/CarstensenGroup_Public/assets/142328197/2e4dd91e-923f-4165-a4d4-611d866d124b">|
| --- | --- | --- |
| For the L-Bracket problem,the passive region should be flush to the force ROI | Proper selection of nodes Passive ROI| Passive ROI overlaps locations of force nodes|

11. 50 Iterations will run automatically
* For the L-Bracket, the 50 iteration output will look like the the figures below, where a stress plot is presented to the user
|<img width="300" alt="image" src="https://github.com/gillschiff/CarstensenGroup_Public/assets/142328197/6e3c766a-0341-47ab-9127-d1aedc40a20d">| <img width="300" alt="image" src="https://github.com/gillschiff/CarstensenGroup_Public/assets/142328197/b1193ebf-76da-4496-91f1-875334cb8bf5">|
| --- | --- |
12. Enter whether you want to make 1 or 2 changes
* For this example, the user will make 2 changes
13. Enter whether you want to specify a new passive ROI (3), max solid ROI (2), min solid (1), or min void (0)?
* For this example, the user will specify a passive void region (3) at the sharp corner in order to reduce the stress concentration.
14. Draw the 1st change ROI
* For the L-Bracket example:
* <img width="300" alt="image" src="https://github.com/gillschiff/CarstensenGroup_Public/assets/142328197/52c3b937-9d60-43b6-aead-51829cc0db4f">

15. Enter which phase you'd like to specify as passive (1) for solid, (0) for void
16. 50 Iterations run automatically
*  If the user decided to only make one change, then the algorithm would run to 2000 iterations or convergence
3. Enter whether you want to specify a new passive ROI (3), max solid ROI (2), min solid (1), or min void (0)?
* For this example, the user's second change will specify a minimum solid length scale in the thin lower, right portion of the L-Bracket.
18. Highlight the ROI on the stress plot.
* The authors have found success when singular members are identified, rather than middle of members.
* <img width="300" alt="image" src="https://github.com/gillschiff/CarstensenGroup_Public/assets/142328197/20c00a0b-29b8-4d43-b748-bccdc0364422">

19. Enter contour lines, lambda (degree of gradation), and new radius
* For this example, the user set contour = 2, radius = 4, and lambda = 5
20. Run until convergence.
<img width="300" alt="image" src="https://github.com/gillschiff/CarstensenGroup_Public/assets/142328197/a3fce988-db77-49f1-8f38-9ac03e1850bd">

Final output

# FishCuT1.2
A semi-automatic MATLAB program that segments 3D images of zebrafish
1.	Acquire microCT images of zebrafish:
1.1.	MicroCT scanning was performed using a vivaCT40 (Scanco Medical, Switzerland). Medium-resolution scans (21 µm voxel resolution) were acquired using the following settings: 55kVp, 145μA, 1024 samples, 500proj/180°, 200 ms integration time. 
1.2.	High-resolution scans (10.5 µm voxel resolution) were acquired using the following settings: 55kVp, 145μA, 2048 samples, 1000proj/180°, 200 ms integration time. DICOM files of individual fish were generated using Scanco software. 
1.3.	In general, at least two fish were scanned simultaneously in each acquisition.
2.	Download the most recent version of FishCuT from the GitHub link: https://github.com/elifesciences-publications/FishCuT.
2.1.	Download FIJI from the program’s homepage.
2.2.	Add the path of the folder containing FishCuT to the environment path.
2.3.	Link Matlab with MIJI.
2.3.1.	Install a recent Java SE Development Kit, which should link through the system’s Matlab Java path.
2.3.2.	Add the path of the Matlab script, Miji.m, contained in the download, to Matlab’s environment. Download and add MIJ.jar to the system’s environment path.
3.	Determine the “IsoData correction factor” to input into FishCuT.
3.1.	Use FIJI to determine an absolute threshold value for bone or use correction factor of 0.73 as found optimal for adult zebrafish.
3.2.	Filter the projection using IsoData.
3.3.	Compute the correction factor by dividing the absolute threshold value for bone by the absolute threshold obtained by IsoData.
3.4.	Average this value across a sample of wild type fish.
4.	Run FishCuT on Matlab. Open Matlab and enter FishCuT in the command line.
4.1.	Enter the preprocessing stage of the program by pressing “Pre-process” on the opening GUI. From the new menu, load the DICOM image.
4.1.1.	Orient the fish so that the skull is upright and pointing towards the left as depicted in the picture on the start window. Either load TIFF or DICOM images and save as a DICOM image.
4.1.2.	Rotate the fish by using the Right, Left, Up, and Down buttons. Use the “Slice Rotator” to rotate the current slice on the screen. Press “Threshold,” then “Binarize.” If the image needs further filtering press “Filter.” Compute the angle and preview the rotation.
4.1.2.1.	Retrieve the angle by using the “Retrieve Angle” button. Use the “Process Rotation” button to transform the fish image. Save this new image as a DICOM to be loaded by the “Start” button.
4.1.3.	To view individual slices check the 3D-viewer box. You can still rotate the fish in this stage.
4.2.	Click “Start,” follow the prompts to input scanning parameters, and navigate to the file containing the scan of the fish.
4.2.1.	Choose to accept the automatic detection of the fish boundary or draw your own by entering “m” and clicking boundary points onto the projection.
4.2.2.	Start vertebral segmentation by entering “v.” Annotate the maximum intensity projection by placing white points at each boundary between centra.
4.2.3.	Enter “m” to cut the connection between the ribs and the pterygiophores and associated fin rays.
NOTE: When entering “v” a second time, the program overwrites the first use, but permanently saves the “m” marks.
4.3.	When satisfied with the automatic separation of vertebrae using the user inputs at the centra, type “e” to move on to “vertebral assignment.”
4.3.1.	Click on components assigned to colors when prompted. Click on multiple components to associate with one vertebrae if the arch(es) or rib(s) are separate colors from the centrum. Enter “b” to reset the components for the current vertebrae.
4.3.2.	Press space to move on to the next vertebrae, and repeat 3.3.1. Enter “b” when the current vertebrae is empty to move to the previous vertebrae.
NOTE: After selecting the number of vertebrae specified in the vertebral segmentation stage, the program automatically computes the properties of each vertebrae and saves the outputs in the same directory as the original image.

# NPV_Algorithm
Create a catalogue of synoptic-scale NPV features (that interact with the jet stream) from gridded data. 

Please reference: Lojko et al., (2024), "An ERA5 Climatology of Synoptic-Scale Negative Potential Vorticity-Jet Interactions over the Western North Atlantic" in review for Weather and Climate Dynamics.  

The first step in the algorithm is to label NPV features in a gridded dataset such as ERA5. Labels are assigned to where PV is negative (i.e., equal to or less than -0.01 PVU). The major axis length-scale is calculated for each label. Once all NPV labels are identified, the script applies a threshold to only retain NPV labels of sufficiently large size (the 98th percentile). 

In the second part, the jet stream is identified where contours of 2 PVU are detected from a PV dataset. The PV field is smoothed to ease identification of circumpolar 2 PVU contours.

In the third part, for each large-scale NPV label retained, the distance to the closest 2 PVU coordinate is calculated. The script only keeps time-steps where NPV labels are within 100 km to the 2 PVU contour (refered to as NPV-jet interaciton events). 

#### The code required for detecting negative potential vorticity interactions with the jet stream is provided. It is not intended to be ran in its entirety when dealing with large data. It is up to the user to modify the code when dealing with large datasets. The use of this script and a detailed description of its use is provided in Lojko et al., (2024), "An ERA5 Climatology of Synoptic-Scale Negative Potential Vorticity-Jet Interactions over the Western North Atlantic". 

Some Notes & Requirements:
1. The code has only been tested on ERA5 data using 3D fields (time, latitude, longitude).
2. The script will need modifications if computing over multiple height levels. 
3. The domain (latitude, longitude) used can be flexible. But the longitude should ideally be changed to -180 to 180 degree format.
4. Assume dimension names and order: time, latitude, longitude 
5. When dealing with large data, it is suggested to coarsen the data. (i.e., from 0.25 degrees to 0.5 degrees) if working over a long time-period. 

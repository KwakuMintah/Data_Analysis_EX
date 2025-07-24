# Analysing Older Datasets

This folder contains work I did on analysing older datasets in order to obtain new information, primarily my work on Grain Size Analysis.

In Polycrystalline structures, grains of various sizes and orientations fit together almost like a jigsaw, with various orientations and sizes within. With the nature of neutron diffraction on ENGIN-X, it can often be hard to determine any useful information from the data, as all orientations are collected into two banks, north and south, and the data is summed together.

The detector banks are made up of 24 smaller detectors, extending to encompass an extra 10° either way, and feed data to 2400 pixels or spectra in the nexus datafile. Joe Kelleher proposed that if you were to seperate the summed spectrum into smaller groups, you could use this to analyse more closely the grains in the material.

This notebook is made up of three main functions.

PeakAcrossBanks detects and fits the peaks in the summed spectrum, then uses this to find and fit to the peaks in the separate spectra. This then retrieves the fitted parameters of each peak across each spectra then saves this all as a Panda Datafile.

<img width="1388" height="541" alt="PaB_351469" src="https://github.com/user-attachments/assets/bd49dd7e-b3e1-408f-a95d-4ecddd822472" />

AnalyseOrientationRelations takes this datafile then correlates each peak against each other to see which ones match the closest. The theory behind this is, the more the peaks correlate in the data, the more likely the two grains are twinning.

<img width="609" height="260" alt="358780" src="https://github.com/user-attachments/assets/37c23433-7d81-47ad-b898-c26bc631bde3" />

As shown here with this Copper dataset, there is quite a high correlation between the 111 and 200 peak (a value of 1.0 represents a perfect correlation in this case), implying the two grains may be close to twinning.

AnalyseGrainSize takes the intensities read for each peak from each detector and orders them, creating a graph of peak intensities irregardless of location. This intends to prove that the larger a grain is within a structure, the larger the range between the intensity values detected and vice versa. This can be represented on a graph with a line fit, where the gradient would be taken as an approximation of the range - a larger gradient meaning a larger grain etc.

<img width="640" height="480" alt="351464_GrainSize_graph" src="https://github.com/user-attachments/assets/1d3008ed-02a6-4972-a4e4-4d43a4f2807c" />

With the steepest gradient, it would be assumed in this case, that the 311 peak is the largest and the 331 is the smallest.

To use this notebook, first replace the paths in the first cell with the locations where you have saved the Summary Txt file, CIF folder, and Grouping Folder from the 'Misc' folder on this repository.

<img width="633" height="167" alt="loc_texts" src="https://github.com/user-attachments/assets/8ded877c-e66d-4e32-a177-a92cb2bc3ac5" />

You can search for the run of your experiment by user, title, or date using this cell.

<img width="1551" height="774" alt="search cell" src="https://github.com/user-attachments/assets/ef4c130b-fd43-4e8b-ae91-f037c4f64d4c" />

Or if you already know the run numbers, you can input the value into the called functions in the final cell here.

<img width="1433" height="132" alt="running_cell" src="https://github.com/user-attachments/assets/0a12e9ce-51ca-43fd-a4b0-d499afaf294d" />

This is also where you can select the grouping file if you wish to group the spectra differently. If you know the locations of the peaks in d-spacing, this can be added under peak_list and the correlation for Orientation Relations can be one of these six options:
- Pearson
- Spearman
- Kendall
- Regression
- Xi (requires newest version of Scipy)
- Weighted Kendall

This is an example of a typical output:
<img width="1550" height="741" alt="image" src="https://github.com/user-attachments/assets/75d87328-1810-4d47-af5e-dba4bd18bfdc" />

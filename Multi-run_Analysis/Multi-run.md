This folder contains the work I did writing code for multi-run analysis.

This has been the main bulk of my work, writing and debugging an algorithm to open, plot, fit peaks to, save, and store multiple runs when provided by a user.

This algorithm searches the internal servers for the nexus and raw file using just the run number, or finds said datafile in a filepath provided by the user. It then takes into account the experiment you wish to investigate, searching the file to find these parameters within. After doing so, it loads the file and converts the units to the d-space, extracting the x and y data. The fileSearch function can also extract data as far back as 2002, though certain features such as retrieving the parameters get worse as you go further back.

At the beginning, you provides the script with the runs you would like to analyse alongside the bank you would like to read data from - bank one, two, or both. The script then takes this, confirming whether or not the runs provided are intended to be a range or separate, before the fileSearch algorithm repeats the process on each run until all the data has been collected.
<img width="246" height="152" alt="choices_one" src="https://github.com/user-attachments/assets/413c327d-d22c-4b44-b8ae-6e96a5980920" />
You can also decide whether or not you would like to fit peaks to the dataset. The default peak fitting algorithm uses scipy find peaks to detect the peak location and lmfit to fit to the data. If the experiment was on a material with a cubic crystal structure, i.e. fcc or bcc, selecting that option will run a function which fits peaks to cubic datasets, much more accurately than the default function. If you already know the peak locations in the d-space, from literature or one of the Manual Peak Fit functions, then you can choose to provide this information to the script.

After this, you can select the experiment being performed in order to obtain the respective parameter for labels, and name the file and HDF the data will be stored in.
<img width="238" height="188" alt="choices_two" src="https://github.com/user-attachments/assets/6cb56ce8-5b2c-48f0-827e-8254d399db5b" />
You can decide whether or not you would like to see a plot of the data, and in that case, choose its name. If the data has a significant background the option to remove it from the raw data or add it to the fitted peaks is here as well.
<img width="248" height="222" alt="choices_three" src="https://github.com/user-attachments/assets/e2178010-d24a-4147-86f3-97d34ffcbf9c" />
Finally, if you would like to copy the raw data to your personal files this option is provided.
<img width="235" height="76" alt="choices_four" src="https://github.com/user-attachments/assets/30bf1a3b-3002-48e2-b78f-387596735b01" />
And if you would like to retrieve the data from your personal files instead of the internal servers, this option is available.

After this, the rest all works in the background to provide data and plots such as these:
<img width="640" height="480" alt="Local_Test_Plot" src="https://github.com/user-attachments/assets/47f4daab-9fa0-4a8d-85bf-f5bb68741d34" />
<img width="640" height="480" alt="Local_Test_Plot_HM" src="https://github.com/user-attachments/assets/ae446ec4-8b4b-40d0-8633-ff82c62519e3" />
<img width="640" height="480" alt="Al_for_Poster_Plot_Peaks" src="https://github.com/user-attachments/assets/dba418a1-5eee-47b9-bffc-cb72640d7ceb" />
<img width="640" height="480" alt="Al_for_Poster_nobg_dat_Plot_Peaks" src="https://github.com/user-attachments/assets/63778899-2f19-41dd-a6af-f7adfd715780" />
<img width="640" height="480" alt="Cu_for_Poster_Plot_Peaks" src="https://github.com/user-attachments/assets/86753929-7b6e-481f-92f3-0e60f37cb10c" />

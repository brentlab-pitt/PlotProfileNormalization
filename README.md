# Plot Profile Normalization and Analysis

The following script will normalize and graph plot profile data from either one condition of data or all conditions (ex. if you have plot profiles for wt condition and for a mutant condition). 

### Creating Plot Profiles with Fiji
Plot profile files can be created using Fiji/ImageJ (Draw line on image, Analyze->Plot Profile, Data->Save Data). Fiji saves these plot profile files in .csv format, with 2 columns of data (Distance_(microns) and Gray_Value), therefore this script assumes all files are .csv format. When saving the plot profile files, use the same name for each file (ex. Values.csv or Values_C1.csv) and save the file in an individual folder for each image analyzed (ex. if you have 10 images, created 10 individual folders in a directory and save the plot profile files into their own folder).


### Opening Prompts
After creating plot profiles, run this script and it will ask you several prompts at the beginning. It will ask you for the number of conditions you intend to analyze. Then it will ask you for the name of each condition, it is essential that the name of the directory holding the plot profile folders is the condition name. For example, if you have 2 conditions (wt vs mutant), label the folder containing the data for wt, 'wt', and label the folder containing the data for mutant, 'mutant'. Then when it prompts you for the name of condition 1, enter 'wt', and for condition 2, enter 'mutant'. Then it will ask you for the name of the plot profile files (remember this should be the same for each individual file and the same across conditions, the default name from Fiji is just 'Values'). If you create multiple plot profiles per image, lets say a plot profile for channel1 and a plot profile for channel2, save all the plot profiles for channel 1 as 'Values_C1' and the plot profiles for channel 2 as 'Values_C2', then when you run this script, if you want to normalize and graph the channel 1 plot profiles, input 'Values_C1' when the script prompts: "What is the name of the plot profile files you want to analyze?". Finally, it will pop up a file explorer window and ask what directory your data is in, if you are analyzing 1 condition, select the directory that contains the individual folders with all your plot profile files, if you are analyzing multiple conditions, select the directory that contains all your condition folders (each condition folder should then contain a folder for each plot profile file you collected). 


### Output Files
This script will output several files in each condition folder: the normalized values (normalized_data_condition_{conditionname}.xlsx), the 95% percentile value for each file (individual_95percentiles_{conditionname}.xlsx), the graph of the normalized plot profiles on a 0-100 point scale with 95% confidence intervals. If you analyzed multiple conditions, it will also output a graph with the normalized data for each condition and save this as a pdf to the directory where all the condition folders are located.


### Troubleshooting
If you are getting empty graphs, double check you are choosing the correct directory and that you are inputing the name of the plot profile names correctly (this is case sensitive). Additionally, if you have extra folders in the directories you are analyzing, this may cause errors, I recommend only having the relevant folders in the directories you are selecting.

### Normalization Process
Y values are normalized by subtracting minimum Y value from all Y-values then dividing by the range of Y (difference between the maximum and minimum values of Y). The same process is down for X. Then interpolation is performed to ensure both X and Y data points have exactly 100 points
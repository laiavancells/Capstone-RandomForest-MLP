# Capstone-RandomForest

This study aims to assess the accuracy and practicality of incorporating machine learning algorithms with instrumented insoles for studying Achilles tendon loading outside laboratory environments by developing an 18 class Random Forest classifier that predicts treadmill incline and walking speed as a function of ground reaction forces (GRFs) data. 


## Description

Instrumented insoles with 3 force sensors were used to collected data from fifteen participants that were asked to perform treadmill exercises at varying treadmill incline (0-25%) and walking speed (0.8-1.6 m/s) conditions, with 5% and 0.4 m/s increment, respectively. The ground reaction forces (GRFs) were recorded at the forefoot, midfoot, and heel positions during 30-second walking exercise phases. In order to ensure consistency across participants, each subject performed the same set of conditions. GRFs were normalized by bodyweight (kg) to standardize the data and ensure accurate comparison between participants. The individual steps were extracted from the time series sequences using a peak detection algorithm. The extracted time series sequences for the steps were then fed into a 18 class Random Forest Classifier. The accuracy of the developed models was evaluated based on their speed and incline prediction performance (80-20 train validation split). This code intends to display the potential of using machine learning and instrumented insoles for predicting Achilles tendon loading during exercise.
 

## Deployment

### Dependencies

Python 3

Pandas

Numpy 

Mat4py

Pickle

Matplotlib.pyplot

Sklearn.multioutput: MultiOutputRegressor

Sklearn.ensemble: RandomForestRegressor

Sklearn.preprocessing: StandardScaler

Sklearn.metrics: mean_squared_error

### Installing

To run this code, you must have Python installed. You can install  the libraries using pip:
-	Pip install pandas
-	Pip install mat4py
- pip install numpy 
- pip install pickle 
- pip install matplotlib

### Executing program
The code can be broken down into the following steps:

Import mat4py package to load matlab data structure into python. Load the data_for_Brigid_7_6_2022.mat file and extract the data_proc dictionary. Remove Sub001 from the data_proc dictionary. Loop through the data_proc dictionary and create individual variables for each subject using their respective key name (i.e., sub_ + key name). Print the subject name and the different step keys (excluding Warmup and Cooldown) for each subject.

<img width="558" alt="Screen Shot 2023-04-11 at 1 09 33 PM" src="https://user-images.githubusercontent.com/121143118/231238116-c9742f18-62fc-43ad-9afa-c831df222d2e.png">

For each subject and step key, extract time points, heel_norms, midfoot_norms, and forefoot_norms data into separate lists and store them into individual variables with the respective subject and step key names.Print the first value of the extracted time points, heel_norms, midfoot_norms, and forefoot_norms data for each subject and step key.

<img width="722" alt="Screen Shot 2023-04-11 at 1 10 06 PM" src="https://user-images.githubusercontent.com/121143118/231238227-69bbbdee-4937-4b62-bc93-bf55455b7a9b.png">

Create a dataframe (df1) from a dictionary (extracted_inclines) containing the extracted incline values for each subject and step key. Reshape df1 to a long format with 'subject' and 'incline_val' columns.

<img width="505" alt="Screen Shot 2023-04-11 at 1 11 46 PM" src="https://user-images.githubusercontent.com/121143118/231238625-31ea91b9-62c0-4e12-9436-95931634cd74.png">

Initialize an empty list (step_data_list) to store the step data. Loop through the data_proc dictionary and extract time points, heel_norms, midfoot_norms, and forefoot_norms data for each subject and step key. Determine the speed of each step using the step_key value (SlowX, MediumX, FastX, or unknown). Create a dictionary for each step with the extracted data (time, heel, midfoot, forefoot, speed).

<img width="817" alt="Screen Shot 2023-04-11 at 1 12 39 PM" src="https://user-images.githubusercontent.com/121143118/231238771-bbe58a41-01a8-4495-a251-c8feb4872489.png">

Append each dictionary to the step_data_list. Create a dataframe (df2) from the step_data_list. Add the incline values to df2 from df1.

<img width="546" alt="Screen Shot 2023-04-11 at 1 13 21 PM" src="https://user-images.githubusercontent.com/121143118/231238924-84000f85-612d-473f-a180-494c46d82e16.png">

Calculate the average value of the heel_norms, midfoot_norms, and forefoot_norms lists for each row of df2 and store the results in new columns (heel_avg, midfoot_avg, forefoot_avg, respectively).

<img width="609" alt="Screen Shot 2023-04-11 at 1 13 59 PM" src="https://user-images.githubusercontent.com/121143118/231239049-dcf6796a-3937-447a-97c2-10641a5560e4.png">

Implement Random Forest Classifier 

<img width="669" alt="Screen Shot 2023-04-11 at 1 14 54 PM" src="https://user-images.githubusercontent.com/121143118/231239247-d29c3676-9500-4f25-8270-512ae8df0696.png">

Evaluate the model 

<img width="488" alt="Screen Shot 2023-04-11 at 1 15 23 PM" src="https://user-images.githubusercontent.com/121143118/231239336-6258ffcb-8920-43ae-907f-8373ba3aa6cc.png">

## Help

If you encounter any issues while using this project, try the following:

- Check that all dependencies are installed correctly
- Make sure that you are using the correct command to run the project

## Authors

Laia Vancells Lopez 

laia.vancellslopez@student.fairfield.edu

## Version History
* 0.1
    * Initial Release

## License

This project is licensed under the laiavancells License - see the LICENSE.md file for details

## Acknowledgments

I would like to thank Dr. Drazan and Dr. Bandara for their valuable feedback and contributions to this project. Their insights and expertise were instrumental in improving the quality of our work.

Note
This code has been written with a specific data file in mind (data_for_Brigid_7_6_2022.mat), and may not work with other data files without modification.

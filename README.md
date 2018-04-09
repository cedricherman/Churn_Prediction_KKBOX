# Churn_Prediction_KKBOX
Churn prediction for music streaming service.

First of all, it is important to explore data made available to us.
There are three files available:
- transactions.csv, see [EDA_Transactions](https://github.com/cedricherman/Churn_Prediction_KKBOX/blob/master/notebooks/KKBOX_Data_Exploration_Transactions.ipynb)
- users_log.csv, see [EDA_UserLog](https://github.com/cedricherman/Churn_Prediction_KKBOX/blob/master/notebooks/KKBOX_Data_Exploration_UserLog.ipynb)
- members.csv (to be updated)

Second, features are engineered based on users listening habits and transactions history:
- [Here](https://github.com/cedricherman/Churn_Prediction_KKBOX/blob/master/notebooks/KKBox_FeatureEng_UserLog_SongLength.ipynb) the average number of songs played over a month for the last 6 months is computed for each
song length percentile (25%,50%,75%,98.5%,100%) and intervals.
- [Similarly](https://github.com/cedricherman/Churn_Prediction_KKBOX/blob/master/notebooks/KKBox_FeatureEng_UserLog_UniqueSong.ipynb), the average number of unique songs played on a monthly basis is derived. 
- [Additionally](https://github.com/cedricherman/Churn_Prediction_KKBOX/blob/master/notebooks/KKBox_FeatureEng_UserLog_TotalSeconds.ipynb), daily listening time in second averaged on a monthly basis is calculated.




It is recomended to have Python 3 installed. This code may break with Python 2.x

### Create a virtual environment (Optional but recommended)
It is common practice to keep your current Root Python environment clean and create a new environment for a new study/project.

#### Using Anaconda
If you have the Anaconda distribution of **Python 3** installed, then run the commands below in your OS console:

- `\usr> conda env create -f environment.yml`
- `\usr> source activate kkbox_churn` (Macs and Linux) OR `\usr> activate blackfriday` (Windows)

#### Using pip and virtualenv
- From your console:
    - `\usr> (sudo) pip install virtualenv`
    - `\usr> virtualenv -p python3 kkbox_churn`
    - `\usr> source kkbox_churn/bin/activate`
- `\usr> pip install -r requirements.txt`


### Jupyter Notebook users
If you want to use Jupyter, no need to add jupyter (core,client,...) to your newly created environment. You can simply add a new environment to your current Jupyter notebook as explained [here](https://stackoverflow.com/questions/39604271/conda-environments-not-showing-up-in-jupyter-notebook#44786736):<br>

(make sure you are in your new environment first otherwise activate it)
`\usr> python -m ipykernel install --user --name kkbox_churn --display-name "What_you_see_in_jupyter"`

Once you start your Jupyter Notebook, look at your menu bar and under kernel->change kernel you will see all of your added environment including  "What_you_see_in_jupyter"

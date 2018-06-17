# Churn_Prediction_KKBOX
Music Streaming Provider Churn Prediction.
"Should I stay or should I go?"

For a quick introduction to this churn prediction problem, see this [notebook](https://github.com/cedricherman/Churn_Prediction_KKBOX/blob/master/notebooks/01_Introduction.ipynb).


First of all, it is important to explore data made available to us.
There are three files available:

- transactions.csv, see [EDA_Transactions](https://github.com/cedricherman/Churn_Prediction_KKBOX/blob/master/notebooks/02_Transactions_EDA_Pandas.ipynb)
- users_log.csv, activity log is ~30GB so a postgresSQL database has been created [here](https://github.com/cedricherman/Churn_Prediction_KKBOX/blob/master/notebooks/03a_UserActivity_Create_DB.ipynb), see [EDA_UserLog_DB](https://github.com/cedricherman/Churn_Prediction_KKBOX/blob/master/notebooks/03b_UserActivity_EDA_DB.ipynb) for user
engagement plot and 
[EDA_UserLog_Pandas](https://github.com/cedricherman/Churn_Prediction_KKBOX/blob/master/notebooks/03b_UserActivity_EDA_Pandas.ipynb)
for a complete data exploration using Pandas (Note that PostgreSQL is preferred)
- members.csv (not taken into account at this time)


Second, features are engineered based on users listening habits and transactions history:

- [Here](https://github.com/cedricherman/Churn_Prediction_KKBOX/blob/master/notebooks/05_UserActivity_Feature_Engineering.ipynb) the average number of songs played over a month for the last 6 months is computed for each
song length percentile (25%,50%,75%,98.5%,100%) and intervals. The average number of unique songs played on a monthly basis is derived. Additionally, daily listening time in second averaged on a monthly basis is calculated.
- [Last](https://github.com/cedricherman/Churn_Prediction_KKBOX/blob/master/notebooks/04_Transactions_Feature_Engineering.ipynb), there are interesting features we can derive based on transaction history such as number of uninterrupted days of membership and ratio of active cancellation for instance.


[Finally](https://github.com/cedricherman/Churn_Prediction_KKBOX/blob/master/notebooks/06_Model_Building.ipynb), we are evaluating our Features on a Logistic Regression model using Lasso regularization. Because of class imbalance 
between churn and no churn, we are using SMOTE upsampling method. We will see that people who have long membership are most likely to churn. In addition, KKBOX should be watching closely users whose membership expired following an active cancellation. Also engagement messages should be sent to users with a continuous drop in song played count (no matter how long each song was played).


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

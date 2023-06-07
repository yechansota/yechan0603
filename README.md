{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 7,
   "id": "7d38aa93",
   "metadata": {
    "scrolled": true
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Requirement already satisfied: seaborn in c:\\users\\b\\anaconda3\\lib\\site-packages (0.12.2)\n",
      "Requirement already satisfied: pandas>=0.25 in c:\\users\\b\\anaconda3\\lib\\site-packages (from seaborn) (1.5.3)\n",
      "Requirement already satisfied: numpy!=1.24.0,>=1.17 in c:\\users\\b\\anaconda3\\lib\\site-packages (from seaborn) (1.23.5)\n",
      "Requirement already satisfied: matplotlib!=3.6.1,>=3.1 in c:\\users\\b\\anaconda3\\lib\\site-packages (from seaborn) (3.7.0)\n",
      "Requirement already satisfied: packaging>=20.0 in c:\\users\\b\\appdata\\roaming\\python\\python310\\site-packages (from matplotlib!=3.6.1,>=3.1->seaborn) (23.1)\n",
      "Requirement already satisfied: pyparsing>=2.3.1 in c:\\users\\b\\anaconda3\\lib\\site-packages (from matplotlib!=3.6.1,>=3.1->seaborn) (3.0.9)\n",
      "Requirement already satisfied: python-dateutil>=2.7 in c:\\users\\b\\appdata\\roaming\\python\\python310\\site-packages (from matplotlib!=3.6.1,>=3.1->seaborn) (2.8.2)\n",
      "Requirement already satisfied: cycler>=0.10 in c:\\users\\b\\anaconda3\\lib\\site-packages (from matplotlib!=3.6.1,>=3.1->seaborn) (0.11.0)\n",
      "Requirement already satisfied: pillow>=6.2.0 in c:\\users\\b\\anaconda3\\lib\\site-packages (from matplotlib!=3.6.1,>=3.1->seaborn) (9.4.0)\n",
      "Requirement already satisfied: kiwisolver>=1.0.1 in c:\\users\\b\\anaconda3\\lib\\site-packages (from matplotlib!=3.6.1,>=3.1->seaborn) (1.4.4)\n",
      "Requirement already satisfied: fonttools>=4.22.0 in c:\\users\\b\\anaconda3\\lib\\site-packages (from matplotlib!=3.6.1,>=3.1->seaborn) (4.25.0)\n",
      "Requirement already satisfied: contourpy>=1.0.1 in c:\\users\\b\\anaconda3\\lib\\site-packages (from matplotlib!=3.6.1,>=3.1->seaborn) (1.0.5)\n",
      "Requirement already satisfied: pytz>=2020.1 in c:\\users\\b\\anaconda3\\lib\\site-packages (from pandas>=0.25->seaborn) (2022.7)\n",
      "Requirement already satisfied: six>=1.5 in c:\\users\\b\\appdata\\roaming\\python\\python310\\site-packages (from python-dateutil>=2.7->matplotlib!=3.6.1,>=3.1->seaborn) (1.16.0)\n",
      "Note: you may need to restart the kernel to use updated packages.\n"
     ]
    }
   ],
   "source": [
    "pip install seaborn"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "id": "23357c63",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Statistics for Data Science with Python - Yechan Kim"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "id": "24d97fa8",
   "metadata": {},
   "outputs": [],
   "source": [
    "## Load Dataset"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 17,
   "id": "6dbbd27a",
   "metadata": {},
   "outputs": [],
   "source": [
    "import pandas as pd\n",
    "#import plotly.express as px\n",
    "import seaborn as sns\n",
    "import matplotlib.pyplot as pyplot\n",
    "import matplotlib.ticker as ticker\n",
    "import scipy.stats"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 18,
   "id": "f98d8460",
   "metadata": {},
   "outputs": [],
   "source": [
    "## Task 1: Get Familiar With Data"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 23,
   "id": "d582c875",
   "metadata": {},
   "outputs": [],
   "source": [
    "# CRIM: per capita crime rate by town\n",
    "# ZN: proportion of residential land zoned for lots over $25,000 sq.ft.\n",
    "# INDUS: proportion of non-retail business acres per town.\n",
    "# CHAS: Charles River dummy variable (1 if tract bounds river; 0 otherwise)\n",
    "# NOX: nitric oxides concentration (parts per 10 million)\n",
    "# RM: average number of rooms per dwelling\n",
    "# AGE: proportion of owner-occupied units built prior to 1940\n",
    "# DIS: weighted distances to five Boston employment centres\n",
    "# RAD: index of accessibility to radial highways\n",
    "# TAX: full-value property-tax rate per $10,000\n",
    "# PTRATIO: pupil-teacher ratio by town\n",
    "# LSTAT: % lower status of the population\n",
    "# MEDV: Median value of owner-occupied homes in $1000's"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 26,
   "id": "122b40dc",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Unnamed: 0</th>\n",
       "      <th>CRIM</th>\n",
       "      <th>ZN</th>\n",
       "      <th>INDUS</th>\n",
       "      <th>CHAS</th>\n",
       "      <th>NOX</th>\n",
       "      <th>RM</th>\n",
       "      <th>AGE</th>\n",
       "      <th>DIS</th>\n",
       "      <th>RAD</th>\n",
       "      <th>TAX</th>\n",
       "      <th>PTRATIO</th>\n",
       "      <th>LSTAT</th>\n",
       "      <th>MEDV</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>count</th>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>mean</th>\n",
       "      <td>252.500000</td>\n",
       "      <td>3.613524</td>\n",
       "      <td>11.363636</td>\n",
       "      <td>11.136779</td>\n",
       "      <td>0.069170</td>\n",
       "      <td>0.554695</td>\n",
       "      <td>6.284634</td>\n",
       "      <td>68.574901</td>\n",
       "      <td>3.795043</td>\n",
       "      <td>9.549407</td>\n",
       "      <td>408.237154</td>\n",
       "      <td>18.455534</td>\n",
       "      <td>12.653063</td>\n",
       "      <td>22.532806</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>std</th>\n",
       "      <td>146.213884</td>\n",
       "      <td>8.601545</td>\n",
       "      <td>23.322453</td>\n",
       "      <td>6.860353</td>\n",
       "      <td>0.253994</td>\n",
       "      <td>0.115878</td>\n",
       "      <td>0.702617</td>\n",
       "      <td>28.148861</td>\n",
       "      <td>2.105710</td>\n",
       "      <td>8.707259</td>\n",
       "      <td>168.537116</td>\n",
       "      <td>2.164946</td>\n",
       "      <td>7.141062</td>\n",
       "      <td>9.197104</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>min</th>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.006320</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.460000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.385000</td>\n",
       "      <td>3.561000</td>\n",
       "      <td>2.900000</td>\n",
       "      <td>1.129600</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>187.000000</td>\n",
       "      <td>12.600000</td>\n",
       "      <td>1.730000</td>\n",
       "      <td>5.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>25%</th>\n",
       "      <td>126.250000</td>\n",
       "      <td>0.082045</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>5.190000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.449000</td>\n",
       "      <td>5.885500</td>\n",
       "      <td>45.025000</td>\n",
       "      <td>2.100175</td>\n",
       "      <td>4.000000</td>\n",
       "      <td>279.000000</td>\n",
       "      <td>17.400000</td>\n",
       "      <td>6.950000</td>\n",
       "      <td>17.025000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>50%</th>\n",
       "      <td>252.500000</td>\n",
       "      <td>0.256510</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>9.690000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.538000</td>\n",
       "      <td>6.208500</td>\n",
       "      <td>77.500000</td>\n",
       "      <td>3.207450</td>\n",
       "      <td>5.000000</td>\n",
       "      <td>330.000000</td>\n",
       "      <td>19.050000</td>\n",
       "      <td>11.360000</td>\n",
       "      <td>21.200000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>75%</th>\n",
       "      <td>378.750000</td>\n",
       "      <td>3.677083</td>\n",
       "      <td>12.500000</td>\n",
       "      <td>18.100000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.624000</td>\n",
       "      <td>6.623500</td>\n",
       "      <td>94.075000</td>\n",
       "      <td>5.188425</td>\n",
       "      <td>24.000000</td>\n",
       "      <td>666.000000</td>\n",
       "      <td>20.200000</td>\n",
       "      <td>16.955000</td>\n",
       "      <td>25.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>max</th>\n",
       "      <td>505.000000</td>\n",
       "      <td>88.976200</td>\n",
       "      <td>100.000000</td>\n",
       "      <td>27.740000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>0.871000</td>\n",
       "      <td>8.780000</td>\n",
       "      <td>100.000000</td>\n",
       "      <td>12.126500</td>\n",
       "      <td>24.000000</td>\n",
       "      <td>711.000000</td>\n",
       "      <td>22.000000</td>\n",
       "      <td>37.970000</td>\n",
       "      <td>50.000000</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "       Unnamed: 0        CRIM          ZN       INDUS        CHAS         NOX  \\\n",
       "count  506.000000  506.000000  506.000000  506.000000  506.000000  506.000000   \n",
       "mean   252.500000    3.613524   11.363636   11.136779    0.069170    0.554695   \n",
       "std    146.213884    8.601545   23.322453    6.860353    0.253994    0.115878   \n",
       "min      0.000000    0.006320    0.000000    0.460000    0.000000    0.385000   \n",
       "25%    126.250000    0.082045    0.000000    5.190000    0.000000    0.449000   \n",
       "50%    252.500000    0.256510    0.000000    9.690000    0.000000    0.538000   \n",
       "75%    378.750000    3.677083   12.500000   18.100000    0.000000    0.624000   \n",
       "max    505.000000   88.976200  100.000000   27.740000    1.000000    0.871000   \n",
       "\n",
       "               RM         AGE         DIS         RAD         TAX     PTRATIO  \\\n",
       "count  506.000000  506.000000  506.000000  506.000000  506.000000  506.000000   \n",
       "mean     6.284634   68.574901    3.795043    9.549407  408.237154   18.455534   \n",
       "std      0.702617   28.148861    2.105710    8.707259  168.537116    2.164946   \n",
       "min      3.561000    2.900000    1.129600    1.000000  187.000000   12.600000   \n",
       "25%      5.885500   45.025000    2.100175    4.000000  279.000000   17.400000   \n",
       "50%      6.208500   77.500000    3.207450    5.000000  330.000000   19.050000   \n",
       "75%      6.623500   94.075000    5.188425   24.000000  666.000000   20.200000   \n",
       "max      8.780000  100.000000   12.126500   24.000000  711.000000   22.000000   \n",
       "\n",
       "            LSTAT        MEDV  \n",
       "count  506.000000  506.000000  \n",
       "mean    12.653063   22.532806  \n",
       "std      7.141062    9.197104  \n",
       "min      1.730000    5.000000  \n",
       "25%      6.950000   17.025000  \n",
       "50%     11.360000   21.200000  \n",
       "75%     16.955000   25.000000  \n",
       "max     37.970000   50.000000  "
      ]
     },
     "execution_count": 26,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "boston_df.describe()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 27,
   "id": "00ee0aa1",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Unnamed: 0</th>\n",
       "      <th>CRIM</th>\n",
       "      <th>ZN</th>\n",
       "      <th>INDUS</th>\n",
       "      <th>CHAS</th>\n",
       "      <th>NOX</th>\n",
       "      <th>RM</th>\n",
       "      <th>AGE</th>\n",
       "      <th>DIS</th>\n",
       "      <th>RAD</th>\n",
       "      <th>TAX</th>\n",
       "      <th>PTRATIO</th>\n",
       "      <th>LSTAT</th>\n",
       "      <th>MEDV</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>0</td>\n",
       "      <td>0.00632</td>\n",
       "      <td>18.0</td>\n",
       "      <td>2.31</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.538</td>\n",
       "      <td>6.575</td>\n",
       "      <td>65.2</td>\n",
       "      <td>4.0900</td>\n",
       "      <td>1.0</td>\n",
       "      <td>296.0</td>\n",
       "      <td>15.3</td>\n",
       "      <td>4.98</td>\n",
       "      <td>24.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>1</td>\n",
       "      <td>0.02731</td>\n",
       "      <td>0.0</td>\n",
       "      <td>7.07</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.469</td>\n",
       "      <td>6.421</td>\n",
       "      <td>78.9</td>\n",
       "      <td>4.9671</td>\n",
       "      <td>2.0</td>\n",
       "      <td>242.0</td>\n",
       "      <td>17.8</td>\n",
       "      <td>9.14</td>\n",
       "      <td>21.6</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>2</td>\n",
       "      <td>0.02729</td>\n",
       "      <td>0.0</td>\n",
       "      <td>7.07</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.469</td>\n",
       "      <td>7.185</td>\n",
       "      <td>61.1</td>\n",
       "      <td>4.9671</td>\n",
       "      <td>2.0</td>\n",
       "      <td>242.0</td>\n",
       "      <td>17.8</td>\n",
       "      <td>4.03</td>\n",
       "      <td>34.7</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>3</td>\n",
       "      <td>0.03237</td>\n",
       "      <td>0.0</td>\n",
       "      <td>2.18</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.458</td>\n",
       "      <td>6.998</td>\n",
       "      <td>45.8</td>\n",
       "      <td>6.0622</td>\n",
       "      <td>3.0</td>\n",
       "      <td>222.0</td>\n",
       "      <td>18.7</td>\n",
       "      <td>2.94</td>\n",
       "      <td>33.4</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>4</td>\n",
       "      <td>0.06905</td>\n",
       "      <td>0.0</td>\n",
       "      <td>2.18</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.458</td>\n",
       "      <td>7.147</td>\n",
       "      <td>54.2</td>\n",
       "      <td>6.0622</td>\n",
       "      <td>3.0</td>\n",
       "      <td>222.0</td>\n",
       "      <td>18.7</td>\n",
       "      <td>5.33</td>\n",
       "      <td>36.2</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>5</th>\n",
       "      <td>5</td>\n",
       "      <td>0.02985</td>\n",
       "      <td>0.0</td>\n",
       "      <td>2.18</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.458</td>\n",
       "      <td>6.430</td>\n",
       "      <td>58.7</td>\n",
       "      <td>6.0622</td>\n",
       "      <td>3.0</td>\n",
       "      <td>222.0</td>\n",
       "      <td>18.7</td>\n",
       "      <td>5.21</td>\n",
       "      <td>28.7</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>6</th>\n",
       "      <td>6</td>\n",
       "      <td>0.08829</td>\n",
       "      <td>12.5</td>\n",
       "      <td>7.87</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.524</td>\n",
       "      <td>6.012</td>\n",
       "      <td>66.6</td>\n",
       "      <td>5.5605</td>\n",
       "      <td>5.0</td>\n",
       "      <td>311.0</td>\n",
       "      <td>15.2</td>\n",
       "      <td>12.43</td>\n",
       "      <td>22.9</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>7</th>\n",
       "      <td>7</td>\n",
       "      <td>0.14455</td>\n",
       "      <td>12.5</td>\n",
       "      <td>7.87</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.524</td>\n",
       "      <td>6.172</td>\n",
       "      <td>96.1</td>\n",
       "      <td>5.9505</td>\n",
       "      <td>5.0</td>\n",
       "      <td>311.0</td>\n",
       "      <td>15.2</td>\n",
       "      <td>19.15</td>\n",
       "      <td>27.1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>8</th>\n",
       "      <td>8</td>\n",
       "      <td>0.21124</td>\n",
       "      <td>12.5</td>\n",
       "      <td>7.87</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.524</td>\n",
       "      <td>5.631</td>\n",
       "      <td>100.0</td>\n",
       "      <td>6.0821</td>\n",
       "      <td>5.0</td>\n",
       "      <td>311.0</td>\n",
       "      <td>15.2</td>\n",
       "      <td>29.93</td>\n",
       "      <td>16.5</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>9</th>\n",
       "      <td>9</td>\n",
       "      <td>0.17004</td>\n",
       "      <td>12.5</td>\n",
       "      <td>7.87</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.524</td>\n",
       "      <td>6.004</td>\n",
       "      <td>85.9</td>\n",
       "      <td>6.5921</td>\n",
       "      <td>5.0</td>\n",
       "      <td>311.0</td>\n",
       "      <td>15.2</td>\n",
       "      <td>17.10</td>\n",
       "      <td>18.9</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   Unnamed: 0     CRIM    ZN  INDUS  CHAS    NOX     RM    AGE     DIS  RAD  \\\n",
       "0           0  0.00632  18.0   2.31   0.0  0.538  6.575   65.2  4.0900  1.0   \n",
       "1           1  0.02731   0.0   7.07   0.0  0.469  6.421   78.9  4.9671  2.0   \n",
       "2           2  0.02729   0.0   7.07   0.0  0.469  7.185   61.1  4.9671  2.0   \n",
       "3           3  0.03237   0.0   2.18   0.0  0.458  6.998   45.8  6.0622  3.0   \n",
       "4           4  0.06905   0.0   2.18   0.0  0.458  7.147   54.2  6.0622  3.0   \n",
       "5           5  0.02985   0.0   2.18   0.0  0.458  6.430   58.7  6.0622  3.0   \n",
       "6           6  0.08829  12.5   7.87   0.0  0.524  6.012   66.6  5.5605  5.0   \n",
       "7           7  0.14455  12.5   7.87   0.0  0.524  6.172   96.1  5.9505  5.0   \n",
       "8           8  0.21124  12.5   7.87   0.0  0.524  5.631  100.0  6.0821  5.0   \n",
       "9           9  0.17004  12.5   7.87   0.0  0.524  6.004   85.9  6.5921  5.0   \n",
       "\n",
       "     TAX  PTRATIO  LSTAT  MEDV  \n",
       "0  296.0     15.3   4.98  24.0  \n",
       "1  242.0     17.8   9.14  21.6  \n",
       "2  242.0     17.8   4.03  34.7  \n",
       "3  222.0     18.7   2.94  33.4  \n",
       "4  222.0     18.7   5.33  36.2  \n",
       "5  222.0     18.7   5.21  28.7  \n",
       "6  311.0     15.2  12.43  22.9  \n",
       "7  311.0     15.2  19.15  27.1  \n",
       "8  311.0     15.2  29.93  16.5  \n",
       "9  311.0     15.2  17.10  18.9  "
      ]
     },
     "execution_count": 27,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "boston_df.head(10)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 25,
   "id": "bc7fbf4a",
   "metadata": {},
   "outputs": [],
   "source": [
    "## Task 2: Create an IBM account"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "6b4ed05c",
   "metadata": {},
   "outputs": [],
   "source": [
    "Skipped as it is optional"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "0bbd1cf0",
   "metadata": {},
   "outputs": [],
   "source": [
    "## Task 3: Load the Dataset in your Jupyter Notebook"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "id": "3cc9ba97",
   "metadata": {},
   "outputs": [],
   "source": [
    "boston_url = 'https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-ST0151EN-SkillsNetwork/labs/boston_housing.csv'"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 15,
   "id": "1c2698c5",
   "metadata": {},
   "outputs": [],
   "source": [
    "boston_df=pd.read_csv(boston_url)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 16,
   "id": "cbe2dfe3",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Unnamed: 0</th>\n",
       "      <th>CRIM</th>\n",
       "      <th>ZN</th>\n",
       "      <th>INDUS</th>\n",
       "      <th>CHAS</th>\n",
       "      <th>NOX</th>\n",
       "      <th>RM</th>\n",
       "      <th>AGE</th>\n",
       "      <th>DIS</th>\n",
       "      <th>RAD</th>\n",
       "      <th>TAX</th>\n",
       "      <th>PTRATIO</th>\n",
       "      <th>LSTAT</th>\n",
       "      <th>MEDV</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>0</td>\n",
       "      <td>0.00632</td>\n",
       "      <td>18.0</td>\n",
       "      <td>2.31</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.538</td>\n",
       "      <td>6.575</td>\n",
       "      <td>65.2</td>\n",
       "      <td>4.0900</td>\n",
       "      <td>1.0</td>\n",
       "      <td>296.0</td>\n",
       "      <td>15.3</td>\n",
       "      <td>4.98</td>\n",
       "      <td>24.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>1</td>\n",
       "      <td>0.02731</td>\n",
       "      <td>0.0</td>\n",
       "      <td>7.07</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.469</td>\n",
       "      <td>6.421</td>\n",
       "      <td>78.9</td>\n",
       "      <td>4.9671</td>\n",
       "      <td>2.0</td>\n",
       "      <td>242.0</td>\n",
       "      <td>17.8</td>\n",
       "      <td>9.14</td>\n",
       "      <td>21.6</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>2</td>\n",
       "      <td>0.02729</td>\n",
       "      <td>0.0</td>\n",
       "      <td>7.07</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.469</td>\n",
       "      <td>7.185</td>\n",
       "      <td>61.1</td>\n",
       "      <td>4.9671</td>\n",
       "      <td>2.0</td>\n",
       "      <td>242.0</td>\n",
       "      <td>17.8</td>\n",
       "      <td>4.03</td>\n",
       "      <td>34.7</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>3</td>\n",
       "      <td>0.03237</td>\n",
       "      <td>0.0</td>\n",
       "      <td>2.18</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.458</td>\n",
       "      <td>6.998</td>\n",
       "      <td>45.8</td>\n",
       "      <td>6.0622</td>\n",
       "      <td>3.0</td>\n",
       "      <td>222.0</td>\n",
       "      <td>18.7</td>\n",
       "      <td>2.94</td>\n",
       "      <td>33.4</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>4</td>\n",
       "      <td>0.06905</td>\n",
       "      <td>0.0</td>\n",
       "      <td>2.18</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.458</td>\n",
       "      <td>7.147</td>\n",
       "      <td>54.2</td>\n",
       "      <td>6.0622</td>\n",
       "      <td>3.0</td>\n",
       "      <td>222.0</td>\n",
       "      <td>18.7</td>\n",
       "      <td>5.33</td>\n",
       "      <td>36.2</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   Unnamed: 0     CRIM    ZN  INDUS  CHAS    NOX     RM   AGE     DIS  RAD  \\\n",
       "0           0  0.00632  18.0   2.31   0.0  0.538  6.575  65.2  4.0900  1.0   \n",
       "1           1  0.02731   0.0   7.07   0.0  0.469  6.421  78.9  4.9671  2.0   \n",
       "2           2  0.02729   0.0   7.07   0.0  0.469  7.185  61.1  4.9671  2.0   \n",
       "3           3  0.03237   0.0   2.18   0.0  0.458  6.998  45.8  6.0622  3.0   \n",
       "4           4  0.06905   0.0   2.18   0.0  0.458  7.147  54.2  6.0622  3.0   \n",
       "\n",
       "     TAX  PTRATIO  LSTAT  MEDV  \n",
       "0  296.0     15.3   4.98  24.0  \n",
       "1  242.0     17.8   9.14  21.6  \n",
       "2  242.0     17.8   4.03  34.7  \n",
       "3  222.0     18.7   2.94  33.4  \n",
       "4  222.0     18.7   5.33  36.2  "
      ]
     },
     "execution_count": 16,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "boston_df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "id": "0af12b39",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Text(0.5, 1.0, \"Median value of owner-occupied homes in $1000's\")"
      ]
     },
     "execution_count": 6,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "iVBORw0KGgoAAAANSUhEUgAAAggAAAHFCAYAAACXYgGUAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjcuMCwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy88F64QAAAACXBIWXMAAA9hAAAPYQGoP6dpAAAy+UlEQVR4nO3deXhU5f3//9dkD1mBACEQtiBbIVBld2FfIouIqCBgQG2raBVcq1VirW0Ql2Ld0CKLZdMWULSCskk/ytLggmitSpWtgFAoBJAgSd7fP/zN/DK5Z0IIIRPx+biuua7Mfe5zn/uce5bX3OfMxGNmJgAAgBLCQt0BAABQ/RAQAACAg4AAAAAcBAQAAOAgIAAAAAcBAQAAOAgIAADAQUAAAAAOAgIAAHCccwFh9uzZ8ng88ng8euedd5zlZqbmzZvL4/GoZ8+elbrtJk2aaNy4cb7777zzTtB+/NB4j+u2bdtC3ZUyPfXUU2revLmioqLk8Xh06NChUHcJZ+BsPIfK+1geN26c4uPjK227PwRn+3nes2fPMtu+//77NXjwYDVo0EAej8fv9bS0r776SsOHD1dycrLi4+PVr18/ffDBBwHrLly4UB06dFBMTIzS0tI0ceJEHT161Kl39OhRTZw4UWlpaYqJiVGHDh20cOHCgPtRVt/OFedcQPBKSEjQiy++6JSvXbtW//73v5WQkHDW+3D++edr/fr1Ov/888/6tiB99NFHuvXWW9WrVy+tXr1a69evr5JxxtnDc6hqDRo0SOvXr1f9+vVDsv0//OEPOnDggIYOHaqoqKig9fbv36+LL75YX3zxhWbOnKlXXnlFBQUF6tmzpz7//HO/uvPmzdOoUaPUqVMnLVu2TDk5OZo9e7aGDx/utDt8+HDNmTNHOTk5WrZsmTp16qRRo0Zp/vz5lb6vPwh2jpk1a5ZJshtuuMFiY2Pt8OHDfsvHjBlj3bp1s5/85CfWo0ePSt1248aNLTs7u1LbrC68x/Xrr78OdVeCmjt3rkmyjRs3hrorVaK4uNi+/fbbUHfjB6e8j+Xs7GyLi4urmk6dw3bs2GFXXXWVpaSkmCSLjIy09PR0u+aaa5y6RUVFvr/j4uKCvp7eddddFhkZadu2bfOVHT582FJSUuyqq67ylRUWFlr9+vWtf//+fuvPmzfPJNmbb77pK/vb3/5mkmz+/Pl+dfv162dpaWlWWFjoK+vRo8c5+1pf0jk7gzBq1ChJ0oIFC3xlhw8f1qJFi3TdddcFXOe7777Tww8/rFatWik6Olp16tTR+PHjtX//fr96J0+e1N13363U1FTVqFFDF110kf7xj3847QWaHt20aZNGjhypJk2aKDY2Vk2aNNGoUaO0fft2v3W9U31r1qzRTTfdpJSUFNWuXVvDhw/X7t27y9z3adOmyePxaOvWrc6ye+65R1FRUfrvf/8rSVqxYoUuu+wyNWzYUDExMWrevLl+8Ytf+JaXpfQpFa+ePXs6p2/y8/N15513qmnTpoqKilKDBg00ceJEHTt27JTbkaSZM2eqffv2iomJUa1atXT55Zfrs88+89vmmDFjJEldunQ55fSkJL377rvq06ePEhISVKNGDXXv3l1/+9vf/PocERGhRx991Ff23//+V2FhYUpKSlJhYaGv/NZbb1WdOnVk/9//PuvZs6fatm2rvLw8XXzxxapRo4aaNWumKVOmqLi4uELHxuPx6JZbbtH06dPVunVrRUdHa86cOUH3r7i4WFOnTvU9nuvWratrr71Wu3btcuouX75cffr0UVJSkmrUqKHWrVsrNzfXr87GjRs1ZMgQ1a5dWzExMcrIyNDEiRN9y8eNG6cmTZo4bT/44IPyeDwB9+X5559XixYtFB0drTZt2jjTucFOMWzatElDhw5VrVq1FBMTo5/+9Kd65ZVXnG1v2LBBF154oW9q+d5779XJkyeDHrNAtm7dqksvvVTx8fFKT0/XHXfcoRMnTvjVOXjwoCZMmKAGDRooKipKzZo1069//Wunnne/Z82apZYtWyo2NlYdO3bUhg0bZGZ69NFH1bRpU8XHx6t3794Bn8MrV65Unz59lJiYqBo1aujCCy/UqlWr/Ors379fP//5z5Wenu57Lbvwwgu1cuXKMvc10CmG03ksBzJ8+HD9/e9/1+OPP64LLrjA9wm9oKDAqRsWVr63pCVLlqh3795q3LixrywxMVHDhw/X66+/7ntubtiwQXv27NH48eP91r/yyisVHx+vJUuW+LUZHx+vK6+80q/u+PHjtXv3bm3cuDFof4qLi/Xwww/7xjQ5OVmZmZl68skny7U/1VaoE0pl8346yMvLs7Fjx1rnzp19y5577jmLi4uz/Px8ZwahqKjIBg4caHFxcfab3/zGVqxYYTNmzLAGDRpYmzZt/D6pZWdnm8fjsbvuusvefvtte+KJJ6xBgwaWmJjolyrXrFljkmzNmjW+sr/85S82efJkW7Jkia1du9YWLlxoPXr0sDp16tj+/fud/WjWrJn98pe/tLfeestmzJhhNWvWtF69epV5DPbv329RUVH261//2q+8sLDQ0tLSbPjw4X7HJDc315YuXWpr1661OXPmWPv27a1ly5b23XffOf0p+akr2IxJjx49/I7tsWPHrEOHDpaSkmJPPPGErVy50p588klLSkqy3r17W3FxcZn78/vf/94k2ahRo+xvf/ubvfTSS9asWTNLSkqyL774wszMPv30U7v//vtNks2aNcvWr19vW7duDdrmO++8Y5GRkXbBBRfYyy+/bK+++qr179/fPB6PLVy40Feva9eufp8+Fi5caDExMebxeOy9997zlbdu3drvk0uPHj2sdu3adt5559n06dNtxYoVNmHCBJNkc+bMqdCxkWQNGjSwzMxMmz9/vq1evdo++eSToPv485//3CTZLbfcYsuXL7fp06dbnTp1LD093e+xNmPGDPN4PNazZ0+bP3++rVy50p599lmbMGGCr87y5cstMjLSMjMzbfbs2bZ69WqbOXOmjRw50lcnOzvbGjdu7PQjJyfHSr/USLL09HRr06aNLViwwJYuXWoDBw40SfaXv/zFVy/Qc2j16tUWFRVlF198sb388su2fPlyGzdunG/svT799FOrUaOGbxuvvfaaDRgwwBo1alTuGYSoqChr3bq1PfbYY7Zy5UqbPHmyeTwe+81vfuOrd/z4ccvMzLS4uDh77LHH7O2337YHHnjAIiIi7NJLL3X2u3Hjxta9e3dbvHixLVmyxFq0aGG1atWySZMm2WWXXWZvvPGGzZs3z+rVq2eZmZl+j4E///nP5vF4bNiwYbZ48WJ7/fXXbfDgwRYeHm4rV6701RswYIDVqVPHXnjhBXvnnXfs1VdftcmTJ/s9tgMJ9Dwv72M5kIMHD5ok+8Mf/uBrq7yzkMFmEL799lvf629pTz/9tEmyzz//3MzMpk+fbpLs008/dep27NjRunXr5rvftWtX69Spk1Pvk08+MUn2/PPPB+1rbm6uhYeHW05Ojq1atcqWL19u06ZNswcffLA8u1ptndMBwfvi4n0R7dSpk40bN87MzAkICxYsMEm2aNEiv/by8vJMkj377LNmZvbZZ5+ZJJs0aZJfPe+U1akCQmmFhYV29OhRi4uLsyeffNLZj5Iv0mZmU6dONUm2Z8+eMo/D8OHDrWHDhn5Tdm+++aZJstdffz3gOsXFxXby5Enbvn27SbLXXnvN6U9FAkJubq6FhYVZXl6eX72//vWvzjRfaf/73/8sNjbWeaHdsWOHRUdH+01Tlhz7U+natavVrVvXjhw54isrLCy0tm3bWsOGDX0vyvfff7/FxsZaQUGBmZndcMMNNnDgQMvMzPS9SfznP/8xSfbCCy/4HQMFON3Rpk0bGzBgQIWOjSRLSkqygwcPnnL/vI/T0o+fjRs3miS77777zMzsyJEjlpiYaBdddFGZQS0jI8MyMjLs+PHjQeucbkCIjY21vXv3+soKCwutVatW1rx5c19ZoOdQq1at7Kc//amdPHnSr83Bgwdb/fr1fY/5q6++Oug2yhsQJNkrr7ziV37ppZday5Ytffe9b0Kl6z3yyCMmyd5++22//U5NTbWjR4/6yl599VWTZB06dPAbg2nTppkk+/jjj83s+zBZq1YtGzJkiN92ioqKrH379n4fhuLj423ixIll7l8gwQJCeR7LgRQWFlp8fLxdfvnlVlBQUCkBwft8y83NdZbNnz/fJNm6devMzOx3v/td0NfL/v37W4sWLXz3zzvvvID7s3v3bpNkv//974P2dfDgwdahQ4fy7NYPyjl7ikGSevTooYyMDM2cOVNbtmxRXl5e0NMLb7zxhpKTkzVkyBAVFhb6bh06dFBqaqpvinPNmjWSpNGjR/utf9VVVykiIuKUfTp69KjuueceNW/eXBEREYqIiFB8fLyOHTvmN2XuNXToUL/7mZmZkuSckiht/Pjx2rVrl9+U4qxZs5SamqqsrCxf2b59+3TjjTcqPT1dERERioyM9E3bBepPRbzxxhtq27atOnTo4HdsBwwYcMor1NevX6/jx487pwvS09PVu3dvZ2q1PI4dO6aNGzdqxIgRfleph4eHa+zYsdq1a5fvQqc+ffro+PHjWrdunaTvp3f79eunvn37asWKFb4ySerbt6/fdlJTU9W5c2e/sszMTL+xO91j07t3b9WsWdN3v6ioyG8975Sv93Fa+rh17txZrVu39h23devWKT8/XxMmTHBOA3h98cUX+ve//63rr79eMTExQY7q6evTp4/q1avnux8eHq6rr75aW7duDXga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TEwscxuJiYm65JJL9OijjyolJUVNmjTR2rVr9eKLLyo5ObmS9vb/16pVK3Xr1k25ubnauXOnXnjhBWd5RkaGfvWrX8nMVKtWLb3++uu+c+unMnbsWI0ZM0YTJkzQFVdcoe3bt2vq1Km+T5xeEydO1KJFi3TJJZdo0qRJyszMVHFxsXbs2KG3335bd9xxR9AnX3Jysh544AHdd999uvbaazVq1CgdOHBAv/nNbxQTE6OcnJwKHZvc3Fz169dPvXr10p133qmoqCg9++yz+uSTT7RgwQK/T4J9+vRRUVGRVq1a5fe1wr59+yonJ0cej8f3hny6zuTYlKVly5b6+c9/rqeeekphYWHKysrStm3b9MADDyg9PV2TJk2SJMXHx+vxxx/XDTfcoL59++pnP/uZ6tWrp61bt2rz5s16+umnJUnPPPOMhgwZoq5du2rSpElq1KiRduzYobfeessXlq+++mpNnjxZI0eO1F133aWCggL98Y9/DBp+U1JS1Lt3bz3wwAOKi4vTs88+q3/9618Bf7mupOeff15ZWVkaMGCAxo0bpwYNGujgwYP67LPP9MEHH+gvf/mLpO9/lW/p0qXq3bu3Jk+erBo1auiZZ54p91dry+vaa6/VM888o+zsbG3btk3t2rXTu+++q9///ve69NJLKxweS4uPj9dTTz2l7OxsHTx4UCNGjFDdunW1f/9+bd68Wfv379dzzz2nw4cPq1evXrrmmmvUqlUrJSQkKC8vT8uXLw8663K2bN++XSNHjtRNN92kzMxMnThxQlu2bFFubq52796tyy67zK/+2rVrfae0ioqKtH37dv31r3+V9P01Zd7XljvvvFN//vOfNWjQID300EOKjo7WlClTVFBQoAcffNDXXnh4uKZOnaqxY8fqF7/4hUaNGqUvv/xSd999t/r166eBAwf66mZlZalfv3666aablJ+fr+bNm2vBggVavny55s6d6zs1G8iQIUPUtm1bdezYUXXq1NH27ds1bdo0NW7cWOedd15lHc6qF7LLI8+S8l7JHuiHkk6ePGmPPfaYtW/f3mJiYiw+Pt5atWplv/jFL+zLL7/01Ttx4oTdcccdVrduXYuJibGuXbva+vXrnav6A12BvWvXLrviiiusZs2alpCQYAMHDrRPPvnEWTfYfpTnmxElvfDCC74rxkv/aJSZ2T//+U/r16+fJSQk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",
      "text/plain": [
       "<Figure size 640x480 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "sns.boxplot(x=boston_df['MEDV']).set_title(\"Median value of owner-occupied homes in $1000's\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 28,
   "id": "832ebef5",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Text(0.5, 1.0, 'Owner-occupied homes')"
      ]
     },
     "execution_count": 28,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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QeHh4S5XBKAlNef7u0XOZgoKCpLjODLGqLa2tiVeEgAA4LxccJjZu3evFi1apNTUVI0ZM0ZfffWVnn/+ee3fv78l6wMAADirkOYMrqys1GuvvaZf/epXys/PV5cuXTRjxgzNmjVLl19++cWqEQAAoEnNCjMJCQmqrKzUTTfdpLfffltjx45VUJDr190DAAABrFlh5rHHHtNdd92lSy+99GLVAwAA0CzNCjP333+/JOmLL77Qm2++qT179shxHKWmpurWW2/lUBMAAGh1zQoz0ukbOT766KMyxqhz584yxujQoUOaP3++li5dqgcffPBi1AkAANCoZi14ee+99/TII4/okUce0eHDh7V//36Vlpb6wsz8+fP1wQcfXKxaAQAAGmjWzMyqVav0gx/8QFlZWX7tcXFxWrx4sUpLS/Xcc8/pu9/9bkvWCAAA0KRmzcz8+c9/1vTp05vsnz59urZt2/aNiwIAADhfzQozBw4cUPfu3ZvsT01NVWlp6TetCQAA4Lw1K8xUVlYqNDS0yf4OHTro5MmT37goAACA89Xss5l++ctfKioqqtG+ioqKb1wQAABAczQrzCQnJ+v5558/5xgAAIDW0qwws2fPnotUBgAAwIXhxkoAAMBqzQozN954o8rLy33bS5Ys0ddff+3bLisrU+/evVusOAAAgHNpVpjZtGmTqqqqfNvLly/XkSNHfNvV1dX67LPPWq46AACAc2hWmDHGnHUbAACgtbFmBgAAWK1ZYcZxHDmO06ANAADALc06NdsYo5kzZ8rj8Ug6fUXge+65R5GRkZLkt54GAACgNTQrzNx1111+MzF33nlno2MAAABaS7PCzIsvvniRygAAALgwzQozs2bNOucYx3H0wgsvXHBBAAAAzdHsmZmUlBT179+f07IBAECb0Kwwc88992jdunXavXu3Zs2apTvvvFNxcXEXqzYAAIBzatap2c8++6z279+vhx56SG+//baSkpJ0++23a9OmTczUAAAAVzRrZkaSPB6P7rjjDt1xxx3au3evXnzxRWVkZOjUqVPatWuXoqKiLkadAc0Yo8rKSrfLANqUMz8TfD6AhsLCwgLmWnDNDjNnqruInjFGtbW1LVUT6qmsrNS4cePcLgNosyZMmOB2CUCbs2HDBoWHh7tdRqto9u0Mqqqq9Jvf/Ebp6enq1auXdu7cqZUrV2rfvn3M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",
      "text/plain": [
       "<Figure size 640x480 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "ax = sns.boxplot(y = 'MEDV', data = boston_df)\n",
    "ax.set_title('Owner-occupied homes')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 29,
   "id": "b19a6c50",
   "metadata": {},
   "outputs": [],
   "source": [
    "### The boxplot above shows the median value for the variable MEDV among with outliers"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 30,
   "id": "dc067d2b",
   "metadata": {},
   "outputs": [],
   "source": [
    "## Question 2: Provide a histogram for the Charles River variable"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 31,
   "id": "3b635550",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Text(0.5, 1.0, 'Number of homes near the Charles River')"
      ]
     },
     "execution_count": 31,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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2rx5syTpu+++07///W/deeedkqQzZ844bzfffLNSU1P17bffumzzr3/96yX1vmnTJjVt2lRt2rRxGR82bJiMMdq0adMlbac4nTp1UrVq1ZzLoaGhql27tvMxOHXqlL744gv9z//8j6pWreqs8/Ly0uDBg3Xs2LEi8yrusZakXr16FRk/97F+7733VL16dfXp08fl8WvZsqXCwsK0ZcsWSVLLli3l6+ure++9V6+++qp++OGHy5pzy5YtddVVVzmX/f39dc011xTppVOnToqIiHDppfD5kpKS4qzdtGmTunbtqqCgIHl5ecnHx0ePPvqofv31V6Wnp7vsu3nz5rrmmmsuq98L6dWrl7y8vFy2Lck5j5I8J92hb9++LsvNmzdXTk6Oy2Px5Zdfqm/fvgoJCXE+ZkOGDFFBQYH+85//uNy/Ro0a6ty58x/ut7yeP/v375ePj498fHwUHh6u6dOnKzExUaNGjfrD+44YMULZ2dlavXq1c2zJkiXy8/PToEGDJJXtsQSlQ9iBW91xxx1q1aqVHn744SLv4ZdUcHCwy7Kvr68qV67svJjw3PGcnJwi9w8LCyt27Ndff5X0+3UKkjRx4kTngbDwNnbsWEkq8pHcS/2k1K+//lpsbUREhHN9SYWEhBQZ8/PzU3Z2tiQpIyNDxpjL2n9xj/WFxs99rH/66ScdP35cvr6+RR7DtLQ05+PXqFEjffjhh6pdu7bGjRunRo0aqVGjRnruuefcMufCXt59990ifTRr1kzS//0st2/frri4OEnSyy+/rM8++0w7duzQww8/LEku25Qu/Wdeknn4+fm57LMkz8lzFQbCgwcPurWvI0eOqEOHDvrf//1fPffcc/rkk0+0Y8cOvfDCCy51hS71MSuv50+jRo20Y8cObd++Xf/85z/VokULJSUladWqVX9432bNmumGG27QkiVLJP1+EfiKFSvUr18/5+ujLI8lKB0+jQW3cjgcmjlzprp16+byUc5ChQHl/IvwSvNL/4+kpaUVO1Z4YK9Zs6YkKTExUbfeemux27j22mtdli/10xIhISFKTU0tMv7jjz+67Lss1KhRQ5UqVSqX/desWVMhISHasGFDsevPPQPVoUMHdejQQQUFBdq5c6fmzp2r+Ph4hYaG6o477nBLL82bN9cTTzxR7PrCoLdq1Sr5+PjovffecwnO69atK/Z+5fkJmZI8J8/VvXt3vfTSS1q3bp3+/ve/u62vdevW6dSpU1qzZo3q1avnHN+zZ0+x9Zf6mJXX88ff31+tW7eWJN1www3q1KmTmjVrpvj4ePXu3dvlDGhxhg8frrFjx+rAgQP64YcflJqaquHDh7vMQyqbYwlKh7ADt+vatau6deum6dOnKzIy0mVdaGio/P39XT65IElvv/12mfXz+uuvKyEhwXlQOXz4sLZu3aohQ4ZI+v3g07hxY3311VeaMWOGW/fdpUsXJSUlaffu3WrVqpVzfNmyZXI4HOrUqZNb93euKlWqqG3btlqzZo2efvpp58ekz549qxUrVqhu3bpue1umd+/eWrVqlQoKCtS2bdtLuo+Xl5fatm2rJk2a6LXXXtPu3bvdEnZ69+6t9evXq1GjRqpRo8YF6xwOh7y9vV3eTsrOznbLd0Wdf7bpcpX2OdmvXz9FR0crKSlJvXv3LvYTWf/617/UoUOHy/ooeOFrqPCMjyQZY/Tyyy9fdo/n8tTzJyQkRE8++aSGDx+uuXPnKjEx8aL1AwcOVEJCgpYuXaoffvhBderUcZ4dlMr2WILSIeygTMycOVMxMTFKT093vn0g/X6wvOuuu7R48WI1atRILVq00Pbt27Vy5coy6yU9PV233HKL7rnnHmVmZmrKlCny9/d3ObC9+OKL6tmzp7p3765hw4apTp06+u2333TgwAHt3r1b//znP0u07wcffFDLli1Tr169NH36dNWrV0/vv/++5s+frzFjxrgtbFxIUlKSunXrpk6dOmnixIny9fXV/PnztW/fPr3++utu+1/lHXfcoddee00333yzHnjgAbVp00Y+Pj46duyYNm/erH79+umWW27RwoULtWnTJvXq1UtXXXWVcnJynB8d79q1q1t6mT59upKTk9W+fXvdf//9uvbaa5WTk6NDhw5p/fr1WrhwoerWratevXpp9uzZGjRokO699179+uuvevrpp11+kZdUdHS01qxZowULFigmJkaVKlVynlG4VKV5Tnp5eWnt2rWKi4tTu3btNGbMGHXq1ElVqlTR4cOH9eabb+rdd99VRkbGZfXUrVs3+fr6auDAgZo0aZJycnK0YMGCy97O+Tz5/BkyZIhmz56tp59+WuPGjVNgYOAFa6tXr65bbrlFS5cu1fHjxzVx4kRVquR6NUhZHUtQOoQdlInrr79eAwcO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",
      "text/plain": [
       "<Figure size 640x480 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "ax2 = sns.countplot(x = 'CHAS', data = boston_df)\n",
    "ax2.set_title('Number of homes near the Charles River')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 32,
   "id": "39776c34",
   "metadata": {},
   "outputs": [],
   "source": [
    "### The histogram shows that the majority of the houses are not near the Charles River"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 33,
   "id": "7da91c99",
   "metadata": {},
   "outputs": [],
   "source": [
    "## Question 3: Provide a boxplot for the MEDV variable vs the AGE variable - Discretize the age variable into three groups of 35 years and younger, between 35 and 50 years and older"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 34,
   "id": "046ec93b",
   "metadata": {},
   "outputs": [],
   "source": [
    "boston_df.loc[(boston_df['AGE'] <= 35), 'Age_Group'] = '35 years and younger'\n",
    "boston_df.loc[(boston_df['AGE'] > 35) & (boston_df['AGE'] < 70), 'Age_Group'] = 'between 35 and 70 years'\n",
    "boston_df.loc[(boston_df['AGE'] >= 70), 'Age_Group'] = '70 years and older'"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 36,
   "id": "6f7e0858",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Text(0.5, 1.0, 'Median value of owner-occupied homes per Age Group')"
      ]
     },
     "execution_count": 36,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "iVBORw0KGgoAAAANSUhEUgAAAtIAAAHFCAYAAADfUR4UAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjcuMCwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy88F64QAAAACXBIWXMAAA9hAAAPYQGoP6dpAABl9UlEQVR4nO3dd1QU198G8GepS0dRBBRBUBCi2LBgATuWWEJiiaJgjVETu8bYKzaMsSdR0QgRTSwxNqygYglqNEaJvcRYsERRFBS47x++zI9lF4RhYVd9PudwdGfu3PnOzO7w7OzdQSGEECAiIiIiogIx0HUBRERERERvIwZpIiIiIiIZGKSJiIiIiGRgkCYiIiIikoFBmoiIiIhIBgZpIiIiIiIZGKSJiIiIiGRgkCYiIiIikoFBmoiIiIhIBgZporfM6tWroVAooFAoEBsbqzZfCIGKFStCoVCgcePGWl23q6srQkNDpcexsbG51vG2ydqv169f13UpeVq0aBEqVqwIExMTKBQKPH78WNclUSEUxWsov8/l0NBQWFpaam29VHALFy6EQqFAlSpVdF0KACA5ORmzZs1C3bp1YWtrC2NjY5QpUwatWrXCTz/9hLS0NF2XqHcYpIneUlZWVli5cqXa9Li4OFy5cgVWVlZFXkPNmjVx9OhR1KxZs8jXRcDp06fx5ZdfokmTJti/fz+OHj1aLMeZig5fQ++3VatWAQDOnTuH48eP67SWS5cuoUaNGpgxYwYaNmyIH3/8Efv378eiRYtQtmxZ9O7dG9OnT9dpjfrISNcFEJE8Xbp0QVRUFJYsWQJra2tp+sqVK+Hn54fk5OQir8Ha2hr16tUr8vXQa+fOnQMA9OvXD3Xq1NFxNUVPCIHU1FSYmZnpupQiw9fQu+n58+cwNzfPs82JEydw5swZtG3bFtu3b8fKlStRt27dYqpQVXp6Ojp27IhHjx7h999/h5eXl8r8zp07Y+LEifjjjz/y7OfVq1dQKBQwMnp/4iWvSBO9pT799FMAwLp166RpT548wcaNG9G7d2+Ny7x8+RLTp09H5cqVYWpqitKlS6NXr164f/++SrtXr15h9OjRcHBwgLm5ORo2bIjff/9drT9NH0ufOHECXbt2haurK8zMzODq6opPP/0UN27cUFk26+PnAwcO4PPPP0epUqVgZ2eHoKAg3L59O89tX7BgARQKBS5fvqw2b8yYMTAxMcGDBw8AAHv27EGHDh1Qrlw5KJVKVKxYEZ999pk0Py85h7Jkady4sdqwmeTkZIwcORIVKlSAiYkJypYti6FDhyIlJeWN6wFeX5mqVq0alEolSpYsiY8++giJiYkq6wwODgYA1K1bFwqFQmNt2R0+fBjNmjWDlZUVzM3NUb9+fWzfvl2lZiMjI8ydO1ea9uDBAxgYGMDGxgbp6enS9C+//BKlS5eGEEKqp0qVKkhISECjRo1gbm4ONzc3zJo1C5mZmbL2jUKhwODBg7F8+XJ4eXnB1NQUa9asyXX7MjMzMWfOHOn5bG9vj549e+LWrVtqbXft2oVmzZrBxsYG5ubm8PLyQlhYmEqb48ePo127drCzs4NSqYS7uzuGDh0qzQ8NDYWrq6ta35MnT4ZCodC4Ld999x08PDxgamoKb29vREdHq7TLbWjHiRMn0L59e5QsWRJKpRI1atTAhg0b1NZ97NgxNGjQAEqlEk5OThg7dixevXqV6z7T5PLly2jTpg0sLS3h7OyMESNGqH2E/+jRIwwcOBBly5aFiYkJ3NzcMG7cOLV2WdsdEREBT09PmJmZwdfXF8eOHYMQAnPnzkWFChVgaWmJpk2banwN7927F82aNYO1tTXMzc3RoEED7Nu3T6XN/fv30b9/fzg7O0vnsgYNGmDv3r15bmvWsfrjjz8QFBQEa2tr2NjYIDg4WO08CADr16+Hn58fLCwsYGlpicDAQLUwmTVE5uzZs2jZsiWsrKzQrFmzPOsAIH2iOGvWLNSvXx/R0dF4/vy5Wrtbt27hk08+gZWVFWxtbdG9e3ckJCRAoVBg9erVKm3z+7zJafPmzTh//jzGjRunFqKzuLi4oGPHjtLjrOfu2rVrMWLECJQtWxampqbSMX3TOQ3QfC4F1F9r169fh0KhwJw5czBjxgyUL18eSqUSvr6+as+NYieI6K0SEREhAIiEhATRo0cPUadOHWnesmXLhIWFhUhOThYffPCBCAgIkOZlZGSIVq1aCQsLCzFlyhSxZ88esWLFClG2bFnh7e0tnj9/LrUNCQkRCoVCjBo1SuzevVvMnz9flC1bVlhbW4uQkBCp3YEDBwQAceDAAWnazz//LCZOnCg2b94s4uLiRHR0tAgICBClS5cW9+/fV9sONzc38cUXX4iYmBixYsUKUaJECdGkSZM898H9+/eFiYmJGDdunMr09PR04eTkJIKCglT2SVhYmNi6dauIi4sTa9asEdWqVROenp7i5cuXavVcu3ZNmubi4qKyvVkCAgJU9m1KSoqoXr26KFWqlJg/f77Yu3ev+Pbbb4WNjY1o2rSpyMzMzHN7Zs6cKQCITz/9VGzfvl38+OOPws3NTdjY2IiLFy8KIYQ4d+6cGD9+vAAgIiIixNGjR8Xly5dz7TM2NlYYGxuLWrVqifXr14stW7aIli1bCoVCIaKjo6V29erVEy1btpQeR0dHC6VSKRQKhYiPj5eme3l5ic6dO6vsAzs7O1GpUiWxfPlysWfPHjFw4EABQKxZs0bWvgEgypYtK3x8fMRPP/0k9u/fL/76669ct7F///4CgBg8eLDYtWuXWL58uShdurRwdnZWea6tWLFCKBQK0bhxY/HTTz+JvXv3iqVLl4qBAwdKbXbt2iWMjY2Fj4+PWL16tdi/f79YtWqV6Nq1q9QmJCREuLi4qNUxadIkkfPXKQDh7OwsvL29xbp168TWrVtFq1atBADx888/S+00vYb2798vTExMRKNGjcT69evFrl27RGhoqHTss5w7d06Ym5tL6/j1119FYGCgKF++vNpzWZOQkBBhYmIivLy8xLx588TevXvFxIkThUKhEFOmTJHavXjxQvj4+AgLCwsxb948sXv3bjFhwgRhZGQk2rRpo7bdLi4uon79+mLTpk1i8+bNwsPDQ5QsWVIMGzZMdOjQQWzbtk1ERUWJMmXKCB8fH5XnwNq1a4VCoRAdO3YUmzZtEr/99pv48MMPhaGhodi7d6/ULjAwUJQuXVp8//33IjY2VmzZskVMnDhR5bmtSdaxcnFxEaNGjRIxMTFi/vz5wsLCQtSoUUPlnDBjxgyhUChE7969xbZt28SmTZuEn5+fsLCwEOfOnVPZj8bGxsLV1VWEhYWJffv2iZiYmDzreP78ubCxsRG1a9cWQrx+jgIQq1evVmn37NkzUbFiRVGyZEmxZMkSERMTI4YNGyYqVKig9nzI7/NGk379+gkA4sKFC3m2yy7ruVu2bFnxySefiK1bt4pt27aJhw8f5uucJoT6uTRLztfatWvXpNdUw4YNxcaNG8XPP/8sateuLYyNjcWRI0fyXbe2MUgTvWWyB+msE1lW2Khdu7YIDQ0VQgi1IL1u3ToBQGzcuFGlv4SEBAFALF26VAghRGJiogAghg0bptIuKipKAHhjkM4pPT1dPHv2TFhYWIhvv/1WbTuyhxkhhJgzZ44AIO7cuZPnfggKChLlypUTGRkZ0rQdO3YIAOK3337TuExmZqZ49eqVuHHjhgAgfv31V7V65ATpsLAwYWBgIBISElTa/fLLLwKA2LFjR67b8d9//wkzMzO1QHLz5k1hamoqunXrplZjzvVoUq9ePWFvby+ePn0qTUtPTxdVqlQR5cqVk8LL+PHjhZmZmUhNTRVCCNG3b1/RqlUr4ePjI4Wpf//9VwAQ33//vco+ACCOHz+usl5vb28RGBgoa98AEDY2NuLRo0dv3L6s52nO58/x48cFAPH1118LIYR4+vSpsLa2Fg0bNszzDY27u7twd3cXL168yLVNQYO0mZmZuHv3rjQtPT1dVK5cWVSsWFGapuk1VLlyZVGjRg3x6tUrlT4//PBD4ejoKD3nu3Tpkus68hukAYgNGzaoTG/Tpo3w9PSUHi9fvlxju9mzZwsAYvfu3Srb7eDgIJ49eyZN27JliwAgqlevrnIMFixYIACIP//8Uwjx+k1XyZIlRbt27VTWk5GRIapVq6Zy0cDS0lIMHTo0z+3TJOtY5XZ+i4yMFEK8fv0ZGRmJL774QqXd06dPhYODg8qbyqz9uGrVqnzX8eOPPwoAYvny5VK/lpaWolGjRirtlixZIgCInTt3qkz/7LPP1AJyfp83mmS9ycs6D2TJOmdm/aSnp0vzsp67/v7+KssU5JxW0CDt5OSk8hpNTk4WJUuWFM2bN89124oah3YQvcUCAgLg7u6OVatW4ezZs0hISMh1WMe2bdtga2uLdu3aIT09XfqpXr06HBwcpI+WDxw4AADo3r27yvKdO3fO17i3Z8+eYcyYMahYsSKMjIxgZGQES0tLpKSkqH2sBwDt27dXeezj4wMAakNBcurVqxdu3bql8lFuREQEHBwc0Lp1a2laUlISBgwYAGdnZxgZGcHY2BguLi4AoLEeObZt24YqVaqgevXqKvs2MDDwjXdkOHr0KF68eKE2TMPZ2RlNmzaV9bFlSkoKjh8/jk8++UTlrgyGhobo0aMHbt26hQsXLgAAmjVrhhcvXuDIkSMAXn+s3qJFCzRv3hx79uyRpgFA8+bNVdbj4OCgNlbbx8dH5dgVdN80bdoUJUqUkB5nZGSoLJc1bCTreZpzv9WpUwdeXl7Sfjty5AiSk5MxcOBAteEXWS5evIgrV66gT58+UCqVuezVgmvWrBnKlCkjPTY0NESXLl1w+fJljcNPgNfDLP7++2/p9Zd929u0aYM7d+5Ix+7AgQO5riO/FAoF2rVrpzIt5zHcv38/LCws8Mknn6i0y9r3OZ+jTZo0gYWFhfQ4a6hA69atVY5B1vSsdR05cgSPHj1CSEiI2jFv1aoVEhISpOFAderUwerVqzF9+nQcO3aswMNZcju/ZT2vYmJikJ6ejp49e6rUolQqERAQoPE1/fHHH+d7/StXroSZmRm6du0KALC0tESnTp1w6NAhXLp0SWoXFxcHKysrtGrVSmX5rKF9WQryvCmIb7/9FsbGxtJPtWrV1Nrk3O6iOKdlCQoKUnmNWllZoV27djh48CAyMjJk91sYDNJEbzGFQoFevXohMjISy5cvh4eHBxo1aqSx7b179/D48WOYmJionBiNjY1x9+5daczww4cPAbwOSdkZGRnBzs7ujTV169YNixcvRt++fRETE4Pff/8dCQkJKF26NF68eKHWPmefpqamAKCxbXatW7eGo6MjIiIiAAD//fcftm7dip49e8LQ0BDA6zG0LVu2xKZNmzB69Gjs27cPv//+O44dO5avdeTXvXv38Oeff6rtVysrKwgh8hyPnbW/HR0d1eY5OTlJ8wviv//+gxAi1z6zr7d+/fowNzfH3r17cfnyZVy/fl0K0sePH8ezZ8+wd+9euLm5oUKFCip9aXo+mJqaquzXgu6bnDW7u7urLDd16lSV+t+037LGvZYrVy7X/ZWfNnLkfA1ln5bbcb137x4AYOTIkWr7bODAgQCg8lrNax35YW5urvbmwdTUFKmpqdLjrPXkfCNib28PIyMjtW0pWbKkymMTE5M8p2etK2vbP/nkE7Vtnz17NoQQePToEYDXY5dDQkKwYsUK+Pn5oWTJkujZsyfu3r2br+3O7fyWtS1ZtdSuXVutlvXr16s9b83NzVW+9J2Xy5cv4+DBg2jbti2EEHj8+DEeP34svVHJupMH8HrfZ3+jlCXntII8bzQpX748APULGN26dUNCQgISEhJyvbNMztdgUZzTsuT2fH/58iWePXsmu9/CeH++Vkn0jgoNDcXEiROxfPlyzJgxI9d2WV/m27Vrl8b5WbdRywpHd+/eRdmyZaX56enpbzwBPnnyBNu2bcOkSZPw1VdfSdPT0tKkX4DaknV1deHChXj8+LF0j9NevXpJbf766y+cOXMGq1evRkhIiDRd0xecNFEqlRrvm/rgwQOUKlVKelyqVCmYmZmp/ALMLnvbnLL29507d9Tm3b59O89lc1OiRAkYGBjk2mf2mkxMTNCwYUPs3bsX5cqVg4ODA6pWrQo3NzcAr79QtG/fPnz44YcFriNrPQXZNznD2m+//aZyDLLeCGTfbzkDcPb9Vrp0aQDI9QpwftsAeT8fNNEU6rKm5famNKvusWPHIigoSGMbT09PqY+81qEtdnZ2OH78OIQQKscnKSkJ6enpsp6jmmT1s2jRolzvZJIVIEuVKoUFCxZgwYIFuHnzJrZu3YqvvvoKSUlJuZ7jssvt/JZ1XLJq+eWXX6RPsPKS26cdmqxatQpCCPzyyy/45Zdf1OavWbMG06dPh6GhIezs7DR+0TvnMS7I80aTFi1a4Pvvv8fWrVsxcuRIabq9vT3s7e0BvP4doen5n3PbC3JOUyqVePLkiVq7gr6mTExMdHZPdAZpordc2bJlMWrUKPz9998qYTGnDz/8ENHR0cjIyMjzFktZ36COiopCrVq1pOkbNmxQuYuDJgqFAkII6apylhUrVhTJx269evXCnDlzsG7dOqxevRp+fn6oXLmySj0A1Or57rvv8tW/q6sr/vzzT5VpFy9exIULF1R+GXz44YeYOXMm7Ozs1K7avomfnx/MzMwQGRmJTp06SdNv3bqF/fv3q32cnh8WFhaoW7cuNm3ahHnz5km3j8vMzERkZCTKlSsHDw8PqX3z5s0xduxYWFlZScM3LCwsUK9ePSxatAi3b99WG9aRX4XZNwBQtWpVjdObNm0KAIiMjETt2rWl6QkJCUhMTMS4ceMAvL7ibmNjg+XLl6Nr164aA4+Hh4c0RGr48OFqz5csrq6uSEpKwr1796RA9/LlS8TExGhsv2/fPpW2GRkZWL9+Pdzd3XO9+u3p6YlKlSrhzJkzmDlzpsY2WZo0aYKtW7dqXIc2NWvWDBs2bMCWLVvw0UcfSdN//PFHab42NGjQALa2tjh//jwGDx6c7+XKly+PwYMHY9++fYiPj8/XMrmd37LOf4GBgTAyMsKVK1cKNGTjTTIyMrBmzRq4u7tjxYoVavO3bduG8PBw7Ny5Ex9++CECAgKwYcMG7Ny5U2XIWs67vxTkeaPJRx99BG9vb8ycORMffvihynm0oApyTnN1dcXPP/+MtLQ06XX38OFDHDlyROMV/k2bNmHu3LnSpyhPnz7Fb7/9hkaNGkmfRBY3Bmmid8CsWbPe2KZr166IiopCmzZtMGTIENSpUwfGxsa4desWDhw4gA4dOuCjjz6Cl5cXgoODsWDBAhgbG6N58+b466+/MG/evDd+dGltbQ1/f3/MnTsXpUqVgqurK+Li4rBy5UrY2tpqaWv/p3LlyvDz80NYWBj++ecffP/992rz3d3d8dVXX0EIgZIlS+K3336Txv6+SY8ePRAcHIyBAwfi448/xo0bNzBnzhzpCmaWoUOHYuPGjfD398ewYcPg4+ODzMxM3Lx5E7t378aIESNyffNia2uLCRMm4Ouvv0bPnj3x6aef4uHDh5gyZQqUSiUmTZoka9+EhYWhRYsWaNKkCUaOHAkTExMsXboUf/31F9atW6cSKJs1a4aMjAzs27dP5XZzzZs3x6RJk6BQKKTgWlCF2Td58fT0RP/+/bFo0SIYGBigdevWuH79OiZMmABnZ2cMGzYMwOuxp+Hh4ejbty+aN2+Ofv36oUyZMrh8+TLOnDmDxYsXAwCWLFmCdu3aoV69ehg2bBjKly+PmzdvIiYmBlFRUQBe37t94sSJ6Nq1K0aNGoXU1FQsXLgw1zeJpUqVQtOmTTFhwgRYWFhg6dKl+Pvvv9VCUE7fffcdWrdujcDAQISGhqJs2bJ49OgREhMTcerUKfz8888AgPHjx2Pr1q1o2rQpJk6cCHNzcyxZsiTft1zMr549e2LJkiUICQnB9evXUbVqVRw+fBgzZ85EmzZtZL/JysnS0hKLFi1CSEgIHj16hE8++QT29va4f/8+zpw5g/v372PZsmV48uQJmjRpgm7duqFy5cqwsrJCQkICdu3alevV2Jw2bdoEIyMjtGjRAufOncOECRNQrVo1dO7cGcDrgDd16lSMGzcOV69eRatWrVCiRAncu3cPv//+OywsLDBlypQCb+POnTtx+/ZtzJ49W+Nt36pUqYLFixdj5cqV+PDDDxESEoJvvvkGwcHBmD59OipWrIidO3dKb94MDP43Qje/zxtNDA0NsWXLFgQGBqJOnTro168fGjdujBIlSuDx48c4fvw4zpw5k+ut8bIryDmtR48e+O677xAcHIx+/frh4cOHmDNnTq6/awwNDdGiRQsMHz4cmZmZmD17NpKTk2UdC63R2dcciUiW/N65IeddO4QQ4tWrV2LevHmiWrVqQqlUCktLS1G5cmXx2WefiUuXLknt0tLSxIgRI4S9vb1QKpWiXr164ujRo2p3sdB0x4Fbt26Jjz/+WJQoUUJYWVmJVq1aib/++ktt2dy2Iz93Asnu+++/l+6Q8OTJE7X558+fFy1atBBWVlaiRIkSolOnTuLmzZsCgJg0aZJaPdnvdJCZmSnmzJkj3NzchFKpFL6+vmL//v0av2n+7NkzMX78eOHp6SlMTEyEjY2NqFq1qhg2bJjKXRVys2LFCuHj4yMt26FDB5VbbGWvMT937RBCiEOHDommTZsKCwsLYWZmJurVq6fxjiaZmZmiVKlSAoD4999/penx8fECgKhZs6baMgEBAeKDDz5Qm67pzhb53TcAxKBBg/K1bUK8vpvD7NmzhYeHhzA2NhalSpUSwcHB4p9//lFru2PHDhEQECAsLCykW8bNnj1bpc3Ro0dF69athY2NjTA1NRXu7u5qd3fYsWOHqF69ujAzMxNubm5i8eLFud61Y9CgQWLp0qXC3d1dGBsbi8qVK4uoqCiVdrk938+cOSM6d+4s7O3thbGxsXBwcBBNmzaV7vKQJT4+XtSrV0+YmpoKBwcHMWrUKOk1kZ+7dlhYWKhN17Q9Dx8+FAMGDBCOjo7CyMhIuLi4iLFjx6rd5UHTMcy648LcuXM1bnv22wEKIURcXJxo27atKFmypDA2NhZly5YVbdu2ldqlpqaKAQMGCB8fH2FtbS3MzMyEp6enmDRpkkhJSclzm7O27eTJk6Jdu3bC0tJSWFlZiU8//VTcu3dPrf2WLVtEkyZNhLW1tTA1NRUuLi7ik08+UbkVX277UZOOHTsKExMTkZSUlGubrl27CiMjI+m1cfPmTREUFCTV+vHHH0t3KMp+5yEh8v+8yc2TJ0/EzJkzRe3atYW1tbUwMjIS9vb2okWLFmLJkiUq+ze345clP+c0IYRYs2aN8PLyEkqlUnh7e4v169fneteO2bNniylTpohy5coJExMTUaNGjTfearCoKYT4/7vrExERkVYoFAoMGjRIuuJN+mHy5MmYMmUK7t+/r7Wx3bowc+ZMjB8/Hjdv3tT6l2T10fXr11GhQgXMnTtXZQy3PuDQDiIiIiI9lfVmrHLlynj16hX279+PhQsXIjg4+L0I0fqOQZqIiIhIT5mbm+Obb77B9evXkZaWhvLly2PMmDEYP368rksjABzaQUREREQkA/8gCxERERGRDAzSREREREQyMEgTEREREcnALxsSFaHMzEzcvn0bVlZWBfoTskRERKQ7Qgg8ffoUTk5OKn/4JicGaaIidPv2bTg7O+u6DCIiIpLhn3/+yfM2gwzSREXIysoKwOsX4pv+vDYRERHph+TkZDg7O0u/x3PDIE1UhLKGc1hbWzNIExERvWXeNCyTXzYkIiIiIpKBQZqIiIiISAYGaSIiIiIiGRikiYiIiIhkYJAmIiIiIpKBQZqIiIiISAYGaSIiIiIiGXgfaSIiypMQAqmpqVrtLy0tDQBgamr6xvu06jOlUvlW109EhcMgTUREeUpNTUVgYKCuy9BLMTExMDMz03UZRKQjHNpBRERERCQDr0gTEVG+pdTsDhgU8ldHxitY/PHT6/5qdAMMjbVQWTHKTIfFqShdV0FEeoBBmoiI8s/ASLvB19D47QvSRET/j0M7iIiIiIhkYJAmIiIiIpKBQZqIiIiISAYGaSIiIiIiGRikiYiIiIhkYJAmIiIiIpKBQZqIiIiISAYGaSIiIiIiGRikiYiIiIhkYJAmIiIiIpKBQZqIiIiISAYGaSIiIiIiGRikiYiIiIhkYJAmIiIiIpKBQZqIiIiISAYGaSIiIiIiGRikiYiIiIhkYJAmIiIiIpKBQZqIiIiISAYGaSIiIiIiGYx0XQAR0ftECIHU1FQAgFKphEKh0HFFRG8nvpZIH/CKNBFRMUpNTUVgYCACAwOlEEBEBcfXEukDBmkiIiIiIhkYpImIiIiIZGCQJiIiIiKSgUGaiIiIiEgGBmkiIiIiIhkYpImIiIiIZGCQJiIiIiKSgUGaiIiIiEgGBmkiIiIiIhkYpImIiIiIZGCQJiIiIiKSgUGaiIiIiEgGBmkiIiIiIhkYpImIiIiIZGCQJiIiIiKSgUGaiIiIiEgGBmkiIiIiIhkYpImIiIiIZGCQJiIiIiKSQadBunHjxhg6dKguS6ACcnV1xYIFC3RdBhEREZHOvfVXpFevXg1bW1tdlyHLhQsX0KRJE5QpUwZKpRJubm4YP348Xr16JbWJjY2FQqFQ+/n77791WHnuGjdurLHetm3bqrRbunQpKlSoAKVSiVq1auHQoUM6qpj0QXx8PDp16oT4+Hhdl0JE9FbIft4s7Dk0t+X1/dy8YsUKNG7cGCtWrNBZDW99kH6bGRsbo2fPnti9ezcuXLiABQsW4IcffsCkSZPU2l64cAF37tyRfipVqqSDit9s06ZNKnX+9ddfMDQ0RKdOnaQ269evx9ChQzFu3Dj88ccfaNSoEVq3bo2bN2/qsHLNsr+poaKRmpqK8PBw3Lt3D+Hh4UhNTdV1SUREei3neXPevHmyz6G5nYP1/dz8+PFjREZGIjMzE5GRkXj8+LFO6tB5kE5PT8fgwYNha2sLOzs7jB8/HkIIaf7Lly8xevRolC1bFhYWFqhbty5iY2MBvL5a26tXLzx58kS68jl58mQsWrQIVatWlfrYsmULFAoFlixZIk0LDAzE2LFjpce//fYbatWqJV0ZnjJlCtLT06X5T548Qf/+/WFvbw9ra2s0bdoUZ86ckeZPnjwZ1atXx9q1a+Hq6gobGxt07doVT58+zXXb3dzc0KtXL1SrVg0uLi5o3749unfvrvHqrL29PRwcHKQfQ0PDXPvNyMhAnz59UKFCBZiZmcHT0xPffvutSpvQ0FB07NgR8+bNg6OjI+zs7DBo0CCV4JiUlIR27drBzMwMFSpUQFRUVK7rzFKyZEmVOvfs2QNzc3OVID1//nz06dMHffv2hZeXFxYsWABnZ2csW7ZMY5/Xr1+HgYEBTpw4oTJ90aJFcHFxkZ4v58+fR5s2bWBpaYkyZcqgR48eePDggdR+165daNiwofRc+/DDD3HlyhWV9SgUCmzYsAGNGzeGUqlEZGQkbty4gXbt2qFEiRKwsLDABx98gB07drxxX1D+REZG4uHDhwCAhw8f5ut5RkT0Pst+3nzw4EGhzqG5nYP1/dw8btw4ZGZmAgAyMzMxfvx4ndRhpJO1ZrNmzRr06dMHx48fx4kTJ9C/f3+4uLigX79+AIBevXrh+vXriI6OhpOTEzZv3oxWrVrh7NmzqF+/PhYsWICJEyfiwoULAABLS0tcu3YNQ4YMwYMHD1CqVCnExcVJ/w4aNAjp6ek4cuQIhg0bBgCIiYlBcHAwFi5ciEaNGuHKlSvo378/AGDSpEkQQqBt27YoWbIkduzYARsbG3z33Xdo1qwZLl68iJIlSwIArly5gi1btmDbtm3477//0LlzZ8yaNQszZszI1764fPkydu3ahaCgILV5NWrUQGpqKry9vTF+/Hg0adIk134yMzNRrlw5bNiwAaVKlcKRI0fQv39/ODo6onPnzlK7AwcOwNHREQcOHMDly5fRpUsXVK9eXdr3oaGh+Oeff7B//36YmJjgyy+/RFJSUr62JcvKlSvRtWtXWFhYAHj9xujkyZP46quvVNq1bNkSR44c0diHq6srmjdvjoiICPj6+krTIyIiEBoaCoVCgTt37iAgIAD9+vXD/Pnz8eLFC4wZMwadO3fG/v37AQApKSkYPnw4qlatipSUFEycOBEfffQRTp8+DQOD/72nHDNmDMLDwxEREQFTU1P0798fL1++xMGDB2FhYYHz58/D0tKyQPuBNLt16xaioqKkN0NCCERFRSEwMBDlypXTcXVFI/uFAn27wpMblTqz1f/eeguP4bso+74X79HzMud5M7uCnkNzOwdXq1ZNr8/NJ06cwNmzZ1Wm/fnnnzhx4oRKTigOCqHDZ1/jxo2RlJSEc+fOQaFQAAC++uorbN26FefPn8eVK1dQqVIl3Lp1C05OTtJyzZs3R506dTBz5kysXr0aQ4cOVbmkL4SAvb09li9fjo8//hg1atRAly5d8M033+DevXs4evQo/P398d9//8HS0hL+/v5o3bq1yhXqyMhIjB49Grdv38b+/fvx0UcfISkpCaamplKbihUrYvTo0ejfvz8mT56MuXPn4u7du7CysgIAjB49GgcPHsSxY8fy3A/169fHqVOnkJaWhv79+2PZsmVSsLtw4QIOHjyIWrVqIS0tDWvXrsXy5csRGxsLf3//fO/rQYMG4d69e/jll18AvA7JsbGxuHLlinR1u3PnzjAwMEB0dDQuXrwIT09PHDt2DHXr1gUA/P333/Dy8sI333yTry+J/v7776hbty6OHz+OOnXqAABu376NsmXLIj4+HvXr15fazpw5E2vWrJHeEOW0YcMGDBgwAHfu3IGpqSnOnDmDGjVq4OrVq3B1dcXEiRNx/PhxxMTESMvcunULzs7OuHDhAjw8PNT6vH//Puzt7XH27FlUqVIF169fR4UKFbBgwQIMGTJEaufj44OPP/5Y45CbnNLS0pCWliY9Tk5OhrOzM548eQJra+s3Lv8+EUJg5MiROHXqFDIyMqTphoaGqFmzJubNmyedF94l//33Hzp06KDrMmRLqdENMDEvXCcZr2BxYs3r/nxDAENjLVRWjF4+h8UfP+m6Csrm119/RYkSJXRdRpHL7byZXX7Pobn1ZWBgAEtLS6SkpOjluTkzMxPt27dHcnKy2jxra2ts3bpV5eKYXMnJybCxsXnj72+dD+2oV6+eygHx8/PDpUuXkJGRgVOnTkEIAQ8PD1haWko/cXFxKh/J56RQKODv74/Y2Fg8fvwY586dw4ABA5CRkYHExETExsaiZs2a0lXFkydPYurUqSrr6NevH+7cuYPnz5/j5MmTePbsGezs7FTaXLt2TaUOV1dXKUQDgKOjY76u4K5fvx6nTp3CTz/9hO3bt2PevHnSPE9PT/Tr1w81a9aEn58fli5dirZt26q00WT58uXw9fVF6dKlYWlpiR9++EFtDPIHH3ygMkQke72JiYkwMjJSeWdXuXLlAn2xc+XKlahSpYoUorPL+SIUQuT5wuzYsSOMjIywefNmAMCqVavQpEkTuLq6Anh9DA8cOKByfCpXrgwA0jG6cuUKunXrBjc3N1hbW6NChQoAoLZfcr6b/fLLLzF9+nQ0aNAAkyZNwp9//plrnWFhYbCxsZF+nJ2dc237vrtx4wYSEhLUfhlkZGQgISEBN27c0FFlRET6KbfzZnb5PYfm1ldmZiaSk5P19tx89OhRjSEaeB1+jx49Wqz16HxoR14yMzNhaGiIkydPqo0JftNH640bN8b333+PQ4cOoVq1arC1tYW/vz/i4uIQGxuLxo0bq6xnypQpGodUKJVKZGZmwtHRURqbnV32YGlsrHpVRaFQSON38pIVtry9vZGRkYH+/ftjxIgRuY6DrlevHiIjI3Ptb8OGDRg2bBjCw8Ph5+cHKysrzJ07F8ePH1dpl1e9WR9UyH3X+fz5c0RHR2Pq1Kkq00uVKgVDQ0PcvXtXZXpSUhLKlCmTa38mJibo0aMHIiIiEBQUhJ9++knlNnyZmZlo164dZs+erbaso6MjAKBdu3ZwdnbGDz/8ACcnJ2RmZqJKlSp4+fKlSvusYShZ+vbti8DAQGzfvh27d+9GWFgYwsPD8cUXX6ita+zYsRg+fLj0OOuKNKlzcXFB7dq1NV6RrlWrFlxcXHRYXdHJ/qnWr7/+CqVSqcNq8ic1NfV/V9EN9PrXRvHItg/elmP4Lsr+vMz+unqX5XbezC6/59Dc+srrirQ+nJv9/PxgbW2tMUzb2NjAz8+vWOvR+Rkx57CHY8eOoVKlSjA0NESNGjWQkZGBpKQkNGrUSOPyJiYmGp9MjRs3xpAhQ/DLL79IoTkgIAB79+7FkSNHVD66r1mzJi5cuICKFStqXEfNmjVx9+5dGBkZSVdAi4oQAq9evcpzvNcff/whhUNNDh06hPr162PgwIHStLyu4Gvi5eWF9PR0nDhxQrqifOHChXx/K3bDhg1IS0tDcHCwynQTExPUqlULe/bswUcffSRN37Nnzxs/7u7bty+qVKmCpUuX4tWrVypvfGrWrImNGzfC1dUVRkbqT+uHDx8iMTER3333nfRcOnz4cL62BXj9ZmfAgAEYMGAAxo4dix9++EFjkDY1NX1vTuiFpVAoMGzYMPTo0UPj9HdxWAeg+uZUqVTCzMxMh9XI8I4elwJ524/hO+hdPV/klNt5U1ObN+2T3PoyMDDAlClTMHLkSFn9FjUDAwNMnjxZ5aJVlilTpmhlWEeB6inWtWnwzz//YPjw4bhw4QLWrVuHRYsWSSHXw8MD3bt3R8+ePbFp0yZcu3YNCQkJmD17tnTXBFdXVzx79gz79u3DgwcP8Pz5cwBAlSpVYGdnh6ioKClIN27cGFu2bMGLFy/QsGFDqYaJEyfixx9/xOTJk3Hu3DkkJiZi/fr10jdAmzdvDj8/P3Ts2BExMTG4fv06jhw5gvHjx6vdSaIgoqKisGHDBiQmJuLq1av4+eefMXbsWHTp0kUKgwsWLMCWLVtw6dIlnDt3DmPHjsXGjRsxePDgXPutWLEiTpw4gZiYGFy8eBETJkxAQkJCgWrz9PREq1at0K9fPxw/fhwnT55E37598/0LY+XKlejYsSPs7OzU5g0fPhwrVqzAqlWrkJiYiGHDhuHmzZsYMGBAnn16eXmhXr16GDNmDD799FOVWgYNGoRHjx7h008/xe+//46rV69i9+7d6N27NzIyMlCiRAnY2dnh+++/x+XLl7F//36NL0JNhg4dipiYGFy7dg2nTp3C/v374eXlla9lKW/lypVD9+7dpROzQqFA9+7dUbZsWR1XRkSkn3KeN7Mr6Dk0t3NwrVq19Prc7Ovrq3J3NuD195lq1qxZ7LXoPEj37NkTL168QJ06dTBo0CB88cUX0h0zgNd3ZujZsydGjBgBT09PtG/fHsePH5c+Lq9fvz4GDBiALl26oHTp0pgzZw6A1wc9ICAAAKQrkD4+PrCxsUGNGjVUBo4HBgZi27Zt2LNnD2rXro169eph/vz50scXCoUCO3bsgL+/P3r37g0PDw907doV169fz3M4wpsYGRlh9uzZqFOnDnx8fDB58mQMGjRI5cbiL1++xMiRI+Hj44NGjRrh8OHD2L59u8ZhKFkGDBiAoKAgdOnSBXXr1sXDhw9Vrk7nV0REBJydnREQEICgoCDp9n9vcvHiRRw+fBh9+vTROL9Lly5YsGABpk6diurVq+PgwYPYsWNHvj4u6tOnD16+fInevXurTHdyckJ8fDwyMjIQGBiIKlWqYMiQIbCxsYGBgYH0JcqTJ0+iSpUqGDZsGObOnZuv/ZCRkYFBgwbBy8sLrVq1gqenJ5YuXZqvZenNgoODpTdcpUqVQvfu3XVcERGRfst53izMOTS3c7C+n5tnzJghXX02MDDA9OnTdVKHTu/aQVRQM2bMQHR0tNptb/RVfr/1+76Lj4/HggULMHToUDRo0EDX5RSpFy9eIDAwEMDrW2++DcMCsteslbtsvO137chW/9tyDN9Fb+NrSZuynzcBFOocmts5WN/PzStWrEBkZCSCg4PRt29frfad39/fOh8jTZQfz549Q2JiIhYtWoRp06bpuhzSsgYNGujlSZqISF/lPG8W5hya2zlY38/Nffv21XqALiidD+0gyo/BgwejYcOGCAgIUBvWQURERKQLvCJNb4XVq1dj9erVui6DiIiISMIr0kREREREMjBIExERERHJwCBNRERERCQDgzQRERERkQwM0kREREREMjBIExERERHJwCBNRERERCQDgzQRERERkQwM0kREREREMjBIExERERHJwCBNRERERCQDgzQRERERkQwM0kREREREMjBIExERERHJwCBNRERERCQDgzQRERERkQxGui6AiOh9olQqERMTI/2fiOTha4n0AYM0EVExUigUMDMz03UZRG89vpZIH3BoBxERERGRDAzSREREREQyMEgTEREREcnAIE1EREREJAODNBERERGRDAzSREREREQyMEgTEREREcnAIE1EREREJAODNBERERGRDAzSREREREQyMEgTEREREcnAIE1EREREJAODNBERERGRDAzSREREREQyMEgTEREREcnAIE1EREREJAODNBERERGRDAzSREREREQyMEgTEREREcnAIE1EREREJIORrgsgIqK3SGZ64fvIeKX5/28LbewDInonMEgTEVG+WZyK0m5/f/yk1f6IiIoTh3YQEREREcnAK9JERJQnpVKJmJgYrfUnhEBaWhoAwNTUFAqFQmt9FzelUqnrEohIhxikiYgoTwqFAmZmZlrt09zcXKv9ERHpAod2EBERERHJwCBNRERERCQDgzQRERERkQwM0kREREREMjBIExERERHJwCBNRERERCQDgzQRERERkQwM0kREREREMjBIExERERHJwCBNRERERCQDgzQRERERkQwM0kREREREMjBIExERERHJwCBNRERERCQDgzQRERERkQwM0kREREREMjBIExERERHJwCBNRERERCQDgzQRERERkQwM0kREREREMhjpugAiIn0jhEBqaqquy8g3IQTS0tIAAKamplAoFDquKH+USuVbUysRkSYM0kREOaSmpiIwMFDXZbzzYmJiYGZmpusyiIhk49AOIiIiIiIZeEWaiCgPS/wfw9RQ6LqMPKVlAIMOlgAALPH/D6aGOi4oD2kZCgw6aKvrMoiItIJBmogoD6aGAko9DqY5mRpCz+vV7zclREQFwaEdREREREQyMEgTEREREcnAIE1EREREJAODNBERERGRDAzSREREREQyMEgTEREREcnAIE1EREREJAODNBERERGRDAzSREREREQyMEgTEREREckg+0+EnzhxAomJiVAoFKhcuTJ8fX21WRcRERERkV4rcJC+desWPv30U8THx8PW1hYA8PjxY9SvXx/r1q2Ds7OztmskIiIiItI7BR7a0bt3b7x69QqJiYl49OgRHj16hMTERAgh0KdPn6KokYiIiIhI7xT4ivShQ4dw5MgReHp6StM8PT2xaNEiNGjQQKvFERERERHpqwJfkS5fvjxevXqlNj09PR1ly5bVSlFERERERPquwEF6zpw5+OKLL3DixAkIIQC8/uLhkCFDMG/ePK0XSERERESkjwo8tCM0NBTPnz9H3bp1YWT0evH09HQYGRmhd+/e6N27t9T20aNH2quUiIiIiEiPFDhIL1iwoAjKICIiIiJ6uxQ4SIeEhBRFHUREREREb5UCB+mbN2/mOb98+fKyiyGiNxNCIDU1FQCgVCqhUCh0XBERvU94DiL6nwIHaVdX1zxfNBkZGYUqiIjylpqaisDAQABATEwMzMzMdFwREb1PeA4i+p8CB+k//vhD5fGrV6/wxx9/YP78+ZgxY4bWCiMiIiIi0mcFDtLV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",
      "text/plain": [
       "<Figure size 640x480 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "ax3 = sns.boxplot(x = 'MEDV', y = 'Age_Group', data = boston_df)\n",
    "ax3.set_title('Median value of owner-occupied homes per Age Group')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "09b0d839",
   "metadata": {},
   "outputs": [],
   "source": [
    "### The boxplot above shows that on average the median value of owner occupied homes is higher when the Age is lower"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 37,
   "id": "367ddcc7",
   "metadata": {},
   "outputs": [],
   "source": [
    "## Question 4: Provide a scatter plot to show the relationship between Nitric oxide concentrations and the proportion of non-retail business acres per town. What can you say about the relationship?"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 38,
   "id": "ce8f9322",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Text(0.5, 1.0, 'Nitric oxide concentration per proportion of non-retail business acres per town')"
      ]
     },
     "execution_count": 38,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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qUTXrl3Fjh07DN4jMzNT/x66e2fXrl1FamqqxeOw534lhG3PektxkLn3r/pPd53Z8l1+6623hEwmE9evX9cv+/e//y0AiCeffFK/rLy8XNSrV08kJycLIey/5ixxKBA9evSoeOONNwQAsXPnTv16a4Fobm6ufh+zZ88Whw8fFocPH9aflHHjxgm5XC6aNGkiUlJSxM6dO8X27dv166reGMaOHStkMpmYOHGi+Oqrr8R3330nXn31VfHGG29YPI61a9cKAKJ///5i8+bNYv369aJ9+/ZCoVCI/fv367ebNGmSUCgU4ujRo0IIIXbu3Cm8vLzE7NmzDfZXNRA9ffq08PPzE3feeadYt26d+Oqrr8SAAQNE48aNjW54r776qpDJZGLChAnim2++ERs3bhRdunQR/v7+4vTp0xaPIz09XURGRorQ0FCxbNkysWPHDrF+/XoxYcIE/ZcwMzNTREdHi7CwMPHOO++Ibdu2iSlTpggAYvLkyfp96S6qJk2aiHvvvVds3rxZbN68WSQkJIjg4GCDoGnbtm1CLpeLxMRE8cEHH4hdu3aJ9957T4waNcrgHAQFBYmEhATx0Ucfie+//148//zzwsvLS8ydO1e/ne4m0qRJEzFmzBjx7bffinXr1onGjRuLZs2a6W/mp0+fFt26dRMRERH660Z3sevKHh0dLXr37i2+/PJL8f3334uLFy+KW7duifHjx4uPP/5Y7Nq1S2zbtk288MILwsvLS3z44Yf6chw+fFioVCpx33336fetO/+mHiK2XkO6G0WLFi3EK6+8IlJTU8WyZcuEr6+vePTRRy1+vkLc/k6FhISIqKgo8eabb4rt27eLqVOnCgDiqaee0m9XXl4u7r33XuHv7y/mzZsnUlNTxerVq0V0dLS48847RWFhoX7bmJgYERkZKe644w7x3nvvid27d4sff/yx2mWw9DnYe75iYmLEiy++KLZv3y6WLVsm/P39Rdu2bUVJSYl+23/9618CgJgyZYrYtm2beOedd0RYWJho1KiRQbDRq1cvUb9+fdGoUSOxfPlysXv3brF3715x7Ngxcccdd4i2bdvqP3PdQ8FUgLBnzx4hl8tF+/btxfr168XmzZtF//79hUwmE5999pl+O9097o477hBPP/202L59u1i9erUIDg4WvXv3tvqZ23KuLly4IN5++20BQCxatMjgejXFnjLZc15DQkJEs2bNxDvvvCNSU1PFk08+KQAYfLfMsXS97Nq1SygUCtGjRw+xfv16sW3bNjF+/HiDzyQzM1MsWrRIABBvv/22/jPUBQArV64UKSkp4uuvvxZ79+4VH374oWjTpo1o0aKFwXVU3UDUlu+GPYFoixYtRFxcnPj444/F3r17xYYNG8Tzzz9v8Fpzgagt929bzq0QQjzxxBPCz89PLFu2TOzevVt88803YvHixQaVM7aU1ZQvvvhCvPLKK2LTpk1i79694rPPPhO9evUSYWFhBteYLc843bmNjo4Ww4cPF19//bX45ptvRHZ2tvj444+FTCYTQ4cOFRs3bhRbtmwRgwcPFt7e3gbB6IABA0RYWJhYtWqV2LNnj9i8ebN45ZVXDL7Xpthzv7L1WW8pDqrq8uXL4umnnxYAxMaNG/XfgdzcXCGEbd/lc+fO6SuDdO69916hUqlEs2bN9Mt++OEHAUBs3bpVCGHfNWeNw4FocXGxuOOOO0SHDh1ERUWFEMJ6ICrE7V9CpmoahPj7V/57771ncl3lG8O+ffsEADFr1ix7DkGUl5eLqKgokZCQYPCrPS8vTzRo0EB07dpVv0yr1Yq2bduK2NhYcebMGREeHi569eplVBNVNRAdOXKkUKlUBrWSZWVlomXLlgY3vLS0NOHj4yOefvppg/3l5eWJiIgIMWLECIvHMmHCBCGXy8WZM2fMbjN9+nQBQPzwww8GyydPnixkMpn47bffhBB/X1QJCQkGx/fjjz8KAGLdunX6ZU2bNhVNmzYVRUVFZt93wIABomHDhvovhM6UKVOEUqkUN2/eFEL8fRO57777DLb7/PPPBQCDX1aDBg0y+XDQlb1p06YGX3xTysrKRGlpqXjsscdE27ZtDdb5+/sbXKs6VR8i9lxDuhvV0qVLDfb55JNPCqVSqf/umKOrCa5ay//4448LLy8vcenSJSHE3zX4GzZsMNhO931bsWKFfllMTIzw9vbWf/bW2FoGc5+DI+frueeeM3gvXXD2ySefCCGEOHv2rNEvdiH+vlnOnDnTqPyVfzTrtG7d2mRNoqkAoXPnzqJBgwYiLy9Pv6ysrEzEx8eLhg0b6j9L3X2yatmWLl0qAIiMjAyj99Ox51zprssvvvjC7P50bC2TI+e16r3lzjvvNGotM8XS97Zly5aibdu2orS01GD54MGDRWRkpP7cfPHFFyYDvKoqKipEaWmpuHTpktG1XN1A1Jbvhq2BaFZWlgAgXn/9davvayoQteX+beu5jY+PF0OHDjVbBlvLaouysjKRn58v/P39DSqSbHnG6c5tz549DZYXFBSI+vXriyFDhhgsLy8vF23atBEdO3bULwsICBDPPvus3eW29X5lz7PeUhxkymuvvWZ0/Qph33e5YcOGYsKECUKI2y1r/v7+Ytq0aQKA/hp+9dVXhVwuF/n5+UII+645axxO36RQKLBw4UL89NNP+Pzzzx3djUlJSUlWt/nuu+8AAE899ZRd+/7tt99w9epVjB07Fl5efx9+QEAAkpKScOTIERQWFgK43U/s888/R3Z2Ntq1awchBNatWwdvb2+L77F7927cc889CA8P1y/z9vbGyJEjDbbbvn07ysrK8Mgjj6CsrEz/T6lUolevXlZHaX/33Xfo3bs3WrVqZXabXbt24c4770THjh0Nlo8fPx5CCOzatctg+aBBgwyOLzExEQD0WRJ+//13/PHHH3jsscegVCpNvqdWq8XOnTsxbNgw+Pn5GRzbfffdB61WiyNHjhi85v777zf4u+r72uL++++HXC43Wv7FF1+gW7duCAgIgI+PD+RyOdasWYOzZ8/avO/K7LmGKpetssTERGi1WmRmZlp9v8DAQKPXjx49GhUVFdi3bx8A4JtvvkG9evUwZMgQg/N91113ISIiwuhaSkxMtGtgiy1l0Kn6OThyvsaMGWPw94gRI+Dj44Pdu3cDgP6/lTNyAEDHjh3RqlUr7Ny502B5cHAw+vTpY/PxVlVQUIAffvgBw4cPR0BAgH65t7c3xo4di/T0dPz2228Gr3HkmnbkXNnDWpnsPa8RERFG95bExESDY9T1+9T9q6ioMCpT5evlwoULOHfunP4aqHr/yMjIMDrXpmRmZmLSpElo1KiR/nsfExMDAA5/902x57thTf369dG0aVO89tprWLZsGY4fP250viyxdv+259x27NgR3333HaZPn449e/agqKjIaWXNz8/HtGnTEBcXBx8fH/j4+CAgIAAFBQUGn40tzzidqnHDoUOHcPPmTYwbN87o+rv33ntx9OhRFBQU6I/1gw8+wMKFC3HkyBGUlpbadBw61u5XjjzrbYmDLLHnu3zPPfdgx44dAG6ft8LCQiQnJyM0NBSpqakAgB07dqBLly7w9/c3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",
      "text/plain": [
       "<Figure size 640x480 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "ax4 = sns.scatterplot(y = 'NOX', x = 'INDUS', data = boston_df)\n",
    "ax4.set_title('Nitric oxide concentration per proportion of non-retail business acres per town')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "e3b46f05",
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.10.9"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}

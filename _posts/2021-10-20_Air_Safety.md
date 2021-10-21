{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 1,
   "metadata": {},
   "outputs": [],
   "source": [
    "# Name: David Selvaraj\n",
    "# Exercise: 4.3\n",
    "# Date: 10-24-2021"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 171,
   "metadata": {
    "scrolled": true
   },
   "outputs": [],
   "source": [
    "import numpy as np\n",
    "import pandas as pd\n",
    "import matplotlib.pyplot as plt\n",
    "import seaborn as sns\n",
    "import squarify\n",
    "pd.options.mode.chained_assignment = None"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 83,
   "metadata": {},
   "outputs": [],
   "source": [
    "# Reading the excel file into a DataFrame\n",
    "\n",
    "home_dir = 'C:/David/Study_MS/DSC640'\n",
    "airline_df = pd.read_csv(home_dir + '/airline-safety.csv')\n",
    "road_crash_df = pd.read_excel(home_dir + '/Car_Crashes.xlsx')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 84,
   "metadata": {},
   "outputs": [],
   "source": [
    "airline_df1 = airline_df[['incidents_85_99','incidents_00_14']]\n",
    "airline_df2 = airline_df[['fatalities_00_14']]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 96,
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
       "      <th>airline</th>\n",
       "      <th>avail_seat_km_per_week</th>\n",
       "      <th>incidents_85_99</th>\n",
       "      <th>fatal_accidents_85_99</th>\n",
       "      <th>fatalities_85_99</th>\n",
       "      <th>incidents_00_14</th>\n",
       "      <th>fatal_accidents_00_14</th>\n",
       "      <th>fatalities_00_14</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>Aer Lingus</td>\n",
       "      <td>320906734</td>\n",
       "      <td>2</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>Aeroflot*</td>\n",
       "      <td>1197672318</td>\n",
       "      <td>76</td>\n",
       "      <td>14</td>\n",
       "      <td>128</td>\n",
       "      <td>6</td>\n",
       "      <td>1</td>\n",
       "      <td>88</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>Aerolineas Argentinas</td>\n",
       "      <td>385803648</td>\n",
       "      <td>6</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>Aeromexico*</td>\n",
       "      <td>596871813</td>\n",
       "      <td>3</td>\n",
       "      <td>1</td>\n",
       "      <td>64</td>\n",
       "      <td>5</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>Air Canada</td>\n",
       "      <td>1865253802</td>\n",
       "      <td>2</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>2</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                 airline  avail_seat_km_per_week  incidents_85_99  \\\n",
       "0             Aer Lingus               320906734                2   \n",
       "1              Aeroflot*              1197672318               76   \n",
       "2  Aerolineas Argentinas               385803648                6   \n",
       "3            Aeromexico*               596871813                3   \n",
       "4             Air Canada              1865253802                2   \n",
       "\n",
       "   fatal_accidents_85_99  fatalities_85_99  incidents_00_14  \\\n",
       "0                      0                 0                0   \n",
       "1                     14               128                6   \n",
       "2                      0                 0                1   \n",
       "3                      1                64                5   \n",
       "4                      0                 0                2   \n",
       "\n",
       "   fatal_accidents_00_14  fatalities_00_14  \n",
       "0                      0                 0  \n",
       "1                      1                88  \n",
       "2                      0                 0  \n",
       "3                      0                 0  \n",
       "4                      0                 0  "
      ]
     },
     "execution_count": 96,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "airline_df.head()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Metrics 1"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 86,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 720x432 with 2 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "fig, ax = plt.subplots(2, figsize=(10, 6))\n",
    "ax[0].scatter(x = airline_df['incidents_85_99'], y = airline_df['fatal_accidents_85_99'])\n",
    "ax[0].set_title('1985 - 1999')\n",
    "ax[0].set_ylabel(\"Fatal Accidents\", color='black', fontweight = 'bold', fontsize = 10)\n",
    "ax[1].scatter(x = airline_df['incidents_00_14'], y = airline_df['fatal_accidents_00_14'])\n",
    "ax[1].set_title('2000 - 2014')\n",
    "ax[1].set_xlabel(\"Incidents\", color='black', fontweight = 'bold', fontsize = 10)\n",
    "ax[1].set_ylabel(\"Fatal Accidents\", color='black', fontweight = 'bold', fontsize = 10)\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Metrics 2"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 87,
   "metadata": {},
   "outputs": [],
   "source": [
    "incidents_df = pd.read_excel(home_dir + '/PersonsKilled_1994_2019_USA.xlsx')\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 88,
   "metadata": {},
   "outputs": [],
   "source": [
    "incidents_df = incidents_df[(incidents_df['Year'] > 1999) & (incidents_df['Year'] < 2015)]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 89,
   "metadata": {},
   "outputs": [],
   "source": [
    "metrics2_df = pd.DataFrame(columns=('Vehicle','Incident_count'))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 90,
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
       "      <th>Year</th>\n",
       "      <th>Passenger Cars</th>\n",
       "      <th>Light Trucks</th>\n",
       "      <th>Large Trucks</th>\n",
       "      <th>Motorcycles</th>\n",
       "      <th>Buses</th>\n",
       "      <th>Other/ Unknown</th>\n",
       "      <th>Total</th>\n",
       "      <th>Pedestrian</th>\n",
       "      <th>Pedalcyclist</th>\n",
       "      <th>Other</th>\n",
       "      <th>Total.1</th>\n",
       "      <th>Unknown Person Type</th>\n",
       "      <th>Total.2</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>6</th>\n",
       "      <td>2000</td>\n",
       "      <td>20699</td>\n",
       "      <td>11526</td>\n",
       "      <td>754</td>\n",
       "      <td>2897</td>\n",
       "      <td>22</td>\n",
       "      <td>450</td>\n",
       "      <td>33451</td>\n",
       "      <td>4763</td>\n",
       "      <td>693</td>\n",
       "      <td>141</td>\n",
       "      <td>5597</td>\n",
       "      <td>0</td>\n",
       "      <td>41945</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>7</th>\n",
       "      <td>2001</td>\n",
       "      <td>20320</td>\n",
       "      <td>11723</td>\n",
       "      <td>708</td>\n",
       "      <td>3197</td>\n",
       "      <td>34</td>\n",
       "      <td>458</td>\n",
       "      <td>33243</td>\n",
       "      <td>4901</td>\n",
       "      <td>732</td>\n",
       "      <td>123</td>\n",
       "      <td>5756</td>\n",
       "      <td>0</td>\n",
       "      <td>42196</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>8</th>\n",
       "      <td>2002</td>\n",
       "      <td>20569</td>\n",
       "      <td>12274</td>\n",
       "      <td>689</td>\n",
       "      <td>3270</td>\n",
       "      <td>45</td>\n",
       "      <td>528</td>\n",
       "      <td>34105</td>\n",
       "      <td>4851</td>\n",
       "      <td>665</td>\n",
       "      <td>114</td>\n",
       "      <td>5630</td>\n",
       "      <td>0</td>\n",
       "      <td>43005</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>9</th>\n",
       "      <td>2003</td>\n",
       "      <td>19725</td>\n",
       "      <td>12546</td>\n",
       "      <td>726</td>\n",
       "      <td>3714</td>\n",
       "      <td>41</td>\n",
       "      <td>589</td>\n",
       "      <td>33627</td>\n",
       "      <td>4774</td>\n",
       "      <td>629</td>\n",
       "      <td>140</td>\n",
       "      <td>5543</td>\n",
       "      <td>0</td>\n",
       "      <td>42884</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>10</th>\n",
       "      <td>2004</td>\n",
       "      <td>19192</td>\n",
       "      <td>12674</td>\n",
       "      <td>766</td>\n",
       "      <td>4028</td>\n",
       "      <td>42</td>\n",
       "      <td>602</td>\n",
       "      <td>33276</td>\n",
       "      <td>4675</td>\n",
       "      <td>727</td>\n",
       "      <td>130</td>\n",
       "      <td>5532</td>\n",
       "      <td>0</td>\n",
       "      <td>42836</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>11</th>\n",
       "      <td>2005</td>\n",
       "      <td>18512</td>\n",
       "      <td>13037</td>\n",
       "      <td>804</td>\n",
       "      <td>4576</td>\n",
       "      <td>58</td>\n",
       "      <td>659</td>\n",
       "      <td>33070</td>\n",
       "      <td>4892</td>\n",
       "      <td>786</td>\n",
       "      <td>186</td>\n",
       "      <td>5864</td>\n",
       "      <td>0</td>\n",
       "      <td>43510</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>12</th>\n",
       "      <td>2006</td>\n",
       "      <td>17925</td>\n",
       "      <td>12761</td>\n",
       "      <td>805</td>\n",
       "      <td>4837</td>\n",
       "      <td>27</td>\n",
       "      <td>601</td>\n",
       "      <td>32119</td>\n",
       "      <td>4795</td>\n",
       "      <td>772</td>\n",
       "      <td>185</td>\n",
       "      <td>5752</td>\n",
       "      <td>0</td>\n",
       "      <td>42708</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>13</th>\n",
       "      <td>2007</td>\n",
       "      <td>16614</td>\n",
       "      <td>12458</td>\n",
       "      <td>805</td>\n",
       "      <td>5174</td>\n",
       "      <td>36</td>\n",
       "      <td>614</td>\n",
       "      <td>30527</td>\n",
       "      <td>4699</td>\n",
       "      <td>701</td>\n",
       "      <td>158</td>\n",
       "      <td>5558</td>\n",
       "      <td>0</td>\n",
       "      <td>41259</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>14</th>\n",
       "      <td>2008</td>\n",
       "      <td>14646</td>\n",
       "      <td>10816</td>\n",
       "      <td>682</td>\n",
       "      <td>5312</td>\n",
       "      <td>67</td>\n",
       "      <td>580</td>\n",
       "      <td>26791</td>\n",
       "      <td>4414</td>\n",
       "      <td>718</td>\n",
       "      <td>188</td>\n",
       "      <td>5320</td>\n",
       "      <td>0</td>\n",
       "      <td>37423</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>15</th>\n",
       "      <td>2009</td>\n",
       "      <td>13135</td>\n",
       "      <td>10312</td>\n",
       "      <td>499</td>\n",
       "      <td>4469</td>\n",
       "      <td>26</td>\n",
       "      <td>554</td>\n",
       "      <td>24526</td>\n",
       "      <td>4109</td>\n",
       "      <td>628</td>\n",
       "      <td>151</td>\n",
       "      <td>4888</td>\n",
       "      <td>0</td>\n",
       "      <td>33883</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>16</th>\n",
       "      <td>2010</td>\n",
       "      <td>12491</td>\n",
       "      <td>9782</td>\n",
       "      <td>530</td>\n",
       "      <td>4518</td>\n",
       "      <td>44</td>\n",
       "      <td>524</td>\n",
       "      <td>23371</td>\n",
       "      <td>4302</td>\n",
       "      <td>623</td>\n",
       "      <td>185</td>\n",
       "      <td>5110</td>\n",
       "      <td>0</td>\n",
       "      <td>32999</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>17</th>\n",
       "      <td>2011</td>\n",
       "      <td>12014</td>\n",
       "      <td>9302</td>\n",
       "      <td>640</td>\n",
       "      <td>4630</td>\n",
       "      <td>55</td>\n",
       "      <td>499</td>\n",
       "      <td>22510</td>\n",
       "      <td>4457</td>\n",
       "      <td>682</td>\n",
       "      <td>200</td>\n",
       "      <td>5339</td>\n",
       "      <td>0</td>\n",
       "      <td>32479</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>18</th>\n",
       "      <td>2012</td>\n",
       "      <td>12361</td>\n",
       "      <td>9418</td>\n",
       "      <td>697</td>\n",
       "      <td>4986</td>\n",
       "      <td>39</td>\n",
       "      <td>502</td>\n",
       "      <td>23017</td>\n",
       "      <td>4818</td>\n",
       "      <td>734</td>\n",
       "      <td>227</td>\n",
       "      <td>5779</td>\n",
       "      <td>0</td>\n",
       "      <td>33782</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>19</th>\n",
       "      <td>2013</td>\n",
       "      <td>12037</td>\n",
       "      <td>9186</td>\n",
       "      <td>695</td>\n",
       "      <td>4692</td>\n",
       "      <td>54</td>\n",
       "      <td>511</td>\n",
       "      <td>22483</td>\n",
       "      <td>4779</td>\n",
       "      <td>749</td>\n",
       "      <td>190</td>\n",
       "      <td>5718</td>\n",
       "      <td>0</td>\n",
       "      <td>32893</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>20</th>\n",
       "      <td>2014</td>\n",
       "      <td>11947</td>\n",
       "      <td>9103</td>\n",
       "      <td>656</td>\n",
       "      <td>4594</td>\n",
       "      <td>44</td>\n",
       "      <td>557</td>\n",
       "      <td>22307</td>\n",
       "      <td>4910</td>\n",
       "      <td>729</td>\n",
       "      <td>204</td>\n",
       "      <td>5843</td>\n",
       "      <td>0</td>\n",
       "      <td>32744</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "    Year  Passenger Cars  Light Trucks  Large Trucks  Motorcycles  Buses  \\\n",
       "6   2000           20699         11526           754         2897     22   \n",
       "7   2001           20320         11723           708         3197     34   \n",
       "8   2002           20569         12274           689         3270     45   \n",
       "9   2003           19725         12546           726         3714     41   \n",
       "10  2004           19192         12674           766         4028     42   \n",
       "11  2005           18512         13037           804         4576     58   \n",
       "12  2006           17925         12761           805         4837     27   \n",
       "13  2007           16614         12458           805         5174     36   \n",
       "14  2008           14646         10816           682         5312     67   \n",
       "15  2009           13135         10312           499         4469     26   \n",
       "16  2010           12491          9782           530         4518     44   \n",
       "17  2011           12014          9302           640         4630     55   \n",
       "18  2012           12361          9418           697         4986     39   \n",
       "19  2013           12037          9186           695         4692     54   \n",
       "20  2014           11947          9103           656         4594     44   \n",
       "\n",
       "    Other/ Unknown  Total  Pedestrian  Pedalcyclist  Other  Total.1  \\\n",
       "6              450  33451        4763           693    141     5597   \n",
       "7              458  33243        4901           732    123     5756   \n",
       "8              528  34105        4851           665    114     5630   \n",
       "9              589  33627        4774           629    140     5543   \n",
       "10             602  33276        4675           727    130     5532   \n",
       "11             659  33070        4892           786    186     5864   \n",
       "12             601  32119        4795           772    185     5752   \n",
       "13             614  30527        4699           701    158     5558   \n",
       "14             580  26791        4414           718    188     5320   \n",
       "15             554  24526        4109           628    151     4888   \n",
       "16             524  23371        4302           623    185     5110   \n",
       "17             499  22510        4457           682    200     5339   \n",
       "18             502  23017        4818           734    227     5779   \n",
       "19             511  22483        4779           749    190     5718   \n",
       "20             557  22307        4910           729    204     5843   \n",
       "\n",
       "    Unknown Person Type   Total.2  \n",
       "6                      0    41945  \n",
       "7                      0    42196  \n",
       "8                      0    43005  \n",
       "9                      0    42884  \n",
       "10                     0    42836  \n",
       "11                     0    43510  \n",
       "12                     0    42708  \n",
       "13                     0    41259  \n",
       "14                     0    37423  \n",
       "15                     0    33883  \n",
       "16                     0    32999  \n",
       "17                     0    32479  \n",
       "18                     0    33782  \n",
       "19                     0    32893  \n",
       "20                     0    32744  "
      ]
     },
     "execution_count": 90,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "incidents_df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 91,
   "metadata": {},
   "outputs": [],
   "source": [
    "value_dict = {'Vehicle':'Cars','Incident_count':incidents_df['Passenger Cars'].sum()}\n",
    "light_truck = {'Vehicle':'Light Trucks','Incident_count':incidents_df['Light Trucks'].sum()}\n",
    "Large_Trucks = {'Vehicle':'Large Trucks','Incident_count':incidents_df['Large Trucks'].sum()}\n",
    "Motorcycle = {'Vehicle':'Motorcycles','Incident_count':incidents_df['Motorcycles'].sum()}\n",
    "Buses = {'Vehicle':'Buses','Incident_count':incidents_df['Buses'].sum()}\n",
    "Air = {'Vehicle':'Air','Incident_count':airline_df['incidents_00_14'].sum()}\n",
    "\n",
    "metrics2_df = metrics2_df.append(value_dict,ignore_index=True)\n",
    "metrics2_df = metrics2_df.append(light_truck,ignore_index=True)\n",
    "metrics2_df = metrics2_df.append(Large_Trucks,ignore_index=True)\n",
    "metrics2_df = metrics2_df.append(Motorcycle,ignore_index=True)\n",
    "metrics2_df = metrics2_df.append(Buses,ignore_index=True)\n",
    "metrics2_df = metrics2_df.append(Air,ignore_index=True)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 92,
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
       "      <th>Vehicle</th>\n",
       "      <th>Incident_count</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>Cars</td>\n",
       "      <td>242187</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>Light Trucks</td>\n",
       "      <td>166918</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>Large Trucks</td>\n",
       "      <td>10456</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>Motorcycles</td>\n",
       "      <td>64894</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>Buses</td>\n",
       "      <td>634</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>5</th>\n",
       "      <td>Air</td>\n",
       "      <td>231</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "        Vehicle Incident_count\n",
       "0          Cars         242187\n",
       "1  Light Trucks         166918\n",
       "2  Large Trucks          10456\n",
       "3   Motorcycles          64894\n",
       "4         Buses            634\n",
       "5           Air            231"
      ]
     },
     "execution_count": 92,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "metrics2_df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 93,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 576x432 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "plt.figure(figsize=(8,6))\n",
    "sns.barplot(x='Vehicle', y='Incident_count', data=metrics2_df)\n",
    "#plt.xticks(rotation=60)\n",
    "plt.ylabel('Incident Count', color='black', fontweight = 'bold', fontsize = 10)\n",
    "plt.xlabel('Vehicle', color='black', fontweight = 'bold', fontsize = 10)\n",
    "plt.title('Incident Count by Vehicle(2000 - 2014)', color='black', fontweight = 'bold', fontsize = 10)\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Metrics 3"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 94,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 720x504 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "fig = plt.figure(figsize=(10,7))\n",
    "#ax = fig.add_axes(['2000-2014','1985-1999'])\n",
    "plt.boxplot(airline_df[['fatalities_00_14','fatalities_85_99']])\n",
    "plt.xticks([1, 2], ['2000-2014', '1985-1999'])\n",
    "plt.ylabel('fatality Count', color='black', fontweight = 'bold', fontsize = 10)\n",
    "#plt.xlabel('Vehicle', color='black', fontweight = 'bold', fontsize = 10)\n",
    "plt.title('Fatality Comparison', color='black', fontweight = 'bold', fontsize = 10)\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Metrics 4"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 126,
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
       "      <th>airline</th>\n",
       "      <th>incidents_85_99</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>51</th>\n",
       "      <td>United / Continental*</td>\n",
       "      <td>11.515152</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>11</th>\n",
       "      <td>American*</td>\n",
       "      <td>12.727273</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>19</th>\n",
       "      <td>Delta / Northwest*</td>\n",
       "      <td>14.545455</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>22</th>\n",
       "      <td>Ethiopian Airlines</td>\n",
       "      <td>15.151515</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>Aeroflot*</td>\n",
       "      <td>46.060606</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                  airline  incidents_85_99\n",
       "51  United / Continental*        11.515152\n",
       "11              American*        12.727273\n",
       "19     Delta / Northwest*        14.545455\n",
       "22     Ethiopian Airlines        15.151515\n",
       "1               Aeroflot*        46.060606"
      ]
     },
     "execution_count": 126,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "treemap_df = airline_df[['airline','incidents_85_99']]\n",
    "treemap_df = treemap_df.sort_values(by=['incidents_85_99'])\n",
    "treemap_df = treemap_df.tail(5)\n",
    "treemap_df['incidents_85_99'] = (100 * treemap_df['incidents_85_99']/treemap_df['incidents_85_99'].sum())#.round(0)\n",
    "treemap_df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 134,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "squarify.plot(sizes=treemap_df['incidents_85_99'], label=treemap_df['airline'], alpha=0.6)\n",
    "plt.title('Top 5 Incidents 1985 - 99', color='black', fontweight = 'bold', fontsize = 12)\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 130,
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
       "      <th>airline</th>\n",
       "      <th>incidents_00_14</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>40</th>\n",
       "      <td>Saudi Arabian</td>\n",
       "      <td>14.285714</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>52</th>\n",
       "      <td>US Airways / America West*</td>\n",
       "      <td>14.285714</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>51</th>\n",
       "      <td>United / Continental*</td>\n",
       "      <td>18.181818</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>11</th>\n",
       "      <td>American*</td>\n",
       "      <td>22.077922</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>19</th>\n",
       "      <td>Delta / Northwest*</td>\n",
       "      <td>31.168831</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                       airline  incidents_00_14\n",
       "40               Saudi Arabian        14.285714\n",
       "52  US Airways / America West*        14.285714\n",
       "51       United / Continental*        18.181818\n",
       "11                   American*        22.077922\n",
       "19          Delta / Northwest*        31.168831"
      ]
     },
     "execution_count": 130,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "treemap_df2 = airline_df[['airline','incidents_00_14']]\n",
    "treemap_df2 = treemap_df2.sort_values(by=['incidents_00_14'])\n",
    "treemap_df2 = treemap_df2.tail(5)\n",
    "treemap_df2['incidents_00_14'] = (100 * treemap_df2['incidents_00_14']/treemap_df2['incidents_00_14'].sum())\n",
    "treemap_df2.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 133,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "squarify.plot(sizes=treemap_df2['incidents_00_14'], label=treemap_df2['airline'], alpha=0.6)\n",
    "plt.title('Top 5 Incidents 2000 - 14', color='black', fontweight = 'bold', fontsize = 12)\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Metrics 5"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 172,
   "metadata": {},
   "outputs": [],
   "source": [
    "metrics5_df = airline_df[['airline','avail_seat_km_per_week']]\n",
    "metrics5_df['Incidents'] = airline_df['incidents_00_14'] + airline_df['incidents_85_99']\n",
    "metrics5_df = metrics5_df.sort_values(by=['avail_seat_km_per_week'])\n",
    "metrics5_df = metrics5_df.tail(10)\n",
    "metrics5_df['avail_seat_km_per_week'] = metrics5_df['avail_seat_km_per_week']/1000000000"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 165,
   "metadata": {},
   "outputs": [],
   "source": [
    "df1 = metrics5_df[['airline','avail_seat_km_per_week']]\n",
    "df1.columns = ('Airline','Count')\n",
    "df1['Description'] = 'Available_Miles'\n",
    "df1\n",
    "df2 = metrics5_df[['airline','Incidents']]\n",
    "df2.columns = ('Airline','Count')\n",
    "df2['Description'] = 'Incidents'\n",
    "frames=[df1,df2]\n",
    "metrics5_final_df = pd.concat(frames)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 164,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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unbtyiqrrMLbb7899bl22203+vTpw+KLL84ll1xS0vdORESKRzX2Jlh88cWZMmUKY8aMYfDgwcw555y89tpr/PHHH6y++upsuOGG3HffffTt25djjz2WyZMn89tvvzF27Fj23HNPhg4dymKLLcYPP/ww9TmHDx/O888/T5s2bRgyZMhf9vf222/z8ssvM378eHr06MHGG2/MWWedxXnnncdDDz0E8JfHnHjiifTo0YNBgwbx9NNPs9NOO01tcfjwww955plnGDduHMssswz77ruvpp+JiFQBBfYmyi2i8/jjj/P2229zzz33APDzzz8zYsQIVlxxRXbbbTcmTpzIZpttRvfu3RkyZAhrrbXW1Ole88wzz9Tn23TTTWnTpk2t++rfvz9t2rShTZs2rLPOOrz66qvMNddc0y3b888/z7333gvAuuuuy/fff8/PP/8MwMYbb8wss8zCLLPMQocOHfj2229ZeOGFm/x+iIhIeSmwN8Fnn31G8+bN6dChA+7OpZdeSt++ff92v6FDh/Lwww+z4447csQRRzDXXHNNd2T4bLPNNt391XzMjEaX17ZyX+4xs8wyy9RtzZs3Z9KkSXU+l4iIVAYF9kYaO3Ys++yzD/vvvz9mRt++fbniiitYd911admyJR9//DELLbQQ3333HQsttBB77rkn48eP5/XXX+fYY49lv/324/PPP5/aFJ9fa5+ewYMHc/TRRzN+/HiGDBnCWWedxejRoxk3blyt919rrbW49dZbOf744xkyZAjt2rVjjjnmKPRbISJSEF+cskJBnqfjCe8U5HkqlQJ7A/z+++90796diRMn0qJFC3bccUcOPfRQAPbYYw9GjhxJz549cXfat2/PoEGDGDJkCOeeey4tW7Zk9tln56abbqJ9+/YMHDiQAQMGMGXKFDp06MATTzwxw/2vtNJKbLzxxnzxxRccf/zxLLjggrRv354WLVrQrVs3dtllF3r06DH1/ieddBK77rorXbt2ZdZZZ+XGG28s2nsjIiLZYLU112ZN7969veZ67B988AHLLbdcmUpUeieddBKzzz47hx9+eLmLUhAz2+cnIjOmGvs0Zjbc3Rs1d1nT3URERKqImuIrxEknnVTuIoiISAVQjV1ERKSKKLCLiIhUEQV2ERGRKqLALiIiUkUU2EVERKpI1YyK73XETQV9vuHn7lSv+91///0MGDCADz74gGWXXbbB+9ljjz049NBD6dy5M506dWLYsGG0a9duuvefffbZ+fXXX/+2fZdddqFfv35sscUWDdr/Lrvswl133cW3335L27ZtATjooIO45JJLGDt2LO3atWO11VbjxRdfZOTIkfTr14933323YS9SRERKRjX2Jrr99ttZY401uOOOOxr1+GuuuYbOnTsXuFQNs+SSSzJ48GAApkyZwjPPPMNCCy009fYXX3yxXEUTEZEGUmBvgl9//ZUXXniBa6+9ljvuuINHH32UrbbaaurtQ4YMYZNNNgFg3333pXfv3nTp0oUTTzxx6n369OlDzax6AJttthm9evWiS5cuDBw48C+3HXbYYfTs2ZP11luPsWPH/u2xw4cPZ+2116ZXr1707duX0aNH1/k6tt12W+68886pZV599dVp0WJaY87ss8/+t8c0dP15EREpDQX2Jhg0aBAbbbQRSy+9NPPMMw/zzjvv1PXSAe6880623nprAE4//XSGDRvG22+/zbPPPsvbb79d53Nfd911DB8+nGHDhnHJJZfw/fffAzB+/Hh69uzJ66+/ztprr83JJ5/8l8dNnDiRAw44gHvuuYfhw4ez2267ceyxx9a5r6WWWoqxY8fy448/cvvtt7PNNtvM8LVfe+21U9eff+2117j66qv5/PPPue222+jbty9vvvkmb731Ft27d5/hc4mISOFUTR97Odx+++0cfPDBAGyzzTbcfffdbLTRRjz44INsscUWPPzww5xzzjkA3HXXXQwcOJBJkyYxevRo3n//fbp27Trd577kkku4//77Afjyyy8ZMWIE8847L82aNZt6srDDDjswYMCAvzzuo48+4t1332WDDTYAoma9wAILzPC1DBgwgDvuuINXXnllau27Lg1Zf15EREpHgb2Rvv/+e55++mneffddzIzJkydjZlx//fVcfvnlzDPPPKy44oq0bduWzz//nPPOO4/XXnuNueeem1122YUJEyZM97mHDBnCk08+yUsvvcSss85Knz59pnv/mmuyuztdunThpZdeatDr2WabbejZsyc777wzzZrNuCGnIevP77RT/QYiiohI06kpvpHuuecedtppJ0aNGsXIkSP58ssvWWyxxWjRogWvv/46V1999dSa9S+//MJss83GnHPOybfffsujjz5a53P//PPPzD333Mw666x8+OGHvPzyy1NvmzJlytRa8m233cYaa6zxl8cus8wyjB07dmpgnzhxIu+9994MX0/Hjh05/fTT+de//lWv159bf37ixIkAfPzxx4wfP55Ro0bRoUMH9txzT3bffXdef/31ej2fiIgURtXU2Os7Pa1Qbr/9do466qi/bNt8882544476NevHzfccMPU9c+7detGjx496NKlC4svvjirr756nc+90UYbceWVV9K1a1eWWWYZVllllam3zTbbbLz33nv06tWLOeecc+qgt5xWrVpxzz33cOCBB/Lzzz8zadIkDj74YLp06TLD17T33nvX9+U3aP15EREpHa3HLmWhz09EatJ67NNoPXYREREBqqgpXuq233778cILL/xl20EHHcSuu+5aphKJiEgxKLDPJC6//PJyF0FEREpATfEiIiJVRIFdRESkiiiwi4iIVBEF9iaobXGU+hg2bBgHHnhgrbd16tSJ7777rlHPO2jQIN5///1GPVZERKpD1QyeK9T8x5xizoPs3bs3vXs3anpinQYNGkS/fv3KvgysiIiUj2rsBTBkyBD69OnDFltswbLLLsv2229PLvHPa6+9xmqrrUa3bt1YaaWVGDduHEOGDKFfv35A5JzfcMMN6dGjB3vvvTf5CYNuueUWVlppJbp3787ee+/N5MmTgWgpOPbYY+nWrRurrLIK3377LS+++CIPPPAARxxxBN27d+fTTz/lkksuoXPnznTt2rVeK7aJiEjlU2AvkDfeeIOLLrqI999/n88++4wXXniBP//8k6233pqLL76Yt956iyeffJI2bdr85XEnn3wya6yxBm+88QabbropX3zxBRCZ2e68805eeOEF3nzzTZo3b86tt94KxNKtq6yyCm+99RZrrbUWV199Nautthqbbrop5557Lm+++SZLLLEEZ511Fm+88QZvv/02V155ZcnfExERKb2qaYovt5VWWomFF14YgO7duzNy5EjmnHNOFlhgAVZccUUA5phjjr89bujQodx3330AbLzxxsw999wAPPXUUwwfPnzqY3///Xc6dOgARD74XI2/V69ePPHEE7WWqWvXrmy//fZsttlmbLbZZoV7sSIiklkK7AUyyyyzTL3cvHlzJk2ahLv/bVnV2tR2H3dn55135swzz/zbbS1btpz6mNy+avPwww8zdOhQHnjgAU499VTee+89WrTQRy4iUs3UFF9E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\n",
      "text/plain": [
       "<Figure size 576x432 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "plt.figure(figsize=(8,6))\n",
    "sns.barplot(x='Airline', y='Count', hue=\"Description\", data=metrics5_final_df, ci=None);\n",
    "plt.xticks(rotation=60)\n",
    "plt.ylabel('Count(Miles in billion)', color='black', fontweight = 'bold', fontsize = 10)\n",
    "plt.xlabel('Airline', color='black', fontweight = 'bold', fontsize = 10)\n",
    "plt.title('Compare Incidents based on Miles', color='black', fontweight = 'bold', fontsize = 10)\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Metrics 6"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 184,
   "metadata": {},
   "outputs": [],
   "source": [
    "metrics6_df = airline_df[['airline']]\n",
    "metrics6_df['Incidents'] = airline_df['incidents_00_14'] + airline_df['incidents_85_99']\n",
    "metrics6_df['Fatal_Accidents'] = airline_df['fatal_accidents_00_14'] + airline_df['fatal_accidents_85_99']\n",
    "metrics6_df['Fatalities'] = airline_df['fatalities_00_14'] + airline_df['fatalities_85_99']\n",
    "metrics6_df = metrics6_df.sort_values(by=['Incidents'])\n",
    "metrics6_df = metrics6_df.tail(5)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 182,
   "metadata": {},
   "outputs": [],
   "source": [
    "metrics6_df['Incidents'] = 100 * (metrics6_df['Incidents'] / (metrics6_df['Incidents'] + metrics6_df['Fatal_Accidents'] + metrics6_df['Fatalities']))\n",
    "metrics6_df['Fatal_Accidents'] = 100 * (metrics6_df['Fatal_Accidents'] / (metrics6_df['Incidents'] + metrics6_df['Fatal_Accidents'] + metrics6_df['Fatalities']))\n",
    "metrics6_df['Fatalities'] = 100 * (metrics6_df['Fatalities'] / (metrics6_df['Incidents'] + metrics6_df['Fatal_Accidents'] + metrics6_df['Fatalities']))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 188,
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
       "      <th>airline</th>\n",
       "      <th>Incidents</th>\n",
       "      <th>Fatal_Accidents</th>\n",
       "      <th>Fatalities</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>22</th>\n",
       "      <td>Ethiopian Airlines</td>\n",
       "      <td>10.135135</td>\n",
       "      <td>2.364865</td>\n",
       "      <td>87.500000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>51</th>\n",
       "      <td>United / Continental*</td>\n",
       "      <td>7.006369</td>\n",
       "      <td>2.123142</td>\n",
       "      <td>90.870488</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>11</th>\n",
       "      <td>American*</td>\n",
       "      <td>6.749556</td>\n",
       "      <td>1.420959</td>\n",
       "      <td>91.829485</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>19</th>\n",
       "      <td>Delta / Northwest*</td>\n",
       "      <td>9.230769</td>\n",
       "      <td>2.692308</td>\n",
       "      <td>88.076923</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>Aeroflot*</td>\n",
       "      <td>26.198083</td>\n",
       "      <td>4.792332</td>\n",
       "      <td>69.009585</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                  airline  Incidents  Fatal_Accidents  Fatalities\n",
       "22     Ethiopian Airlines  10.135135         2.364865   87.500000\n",
       "51  United / Continental*   7.006369         2.123142   90.870488\n",
       "11              American*   6.749556         1.420959   91.829485\n",
       "19     Delta / Northwest*   9.230769         2.692308   88.076923\n",
       "1               Aeroflot*  26.198083         4.792332   69.009585"
      ]
     },
     "execution_count": 188,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "metrics6_df[['Incidents','Fatal_Accidents','Fatalities']] = \\\n",
    "metrics6_df[['Incidents','Fatal_Accidents','Fatalities']].apply(lambda x: x/x.sum() * 100, axis=1)\n",
    "\n",
    "metrics6_df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 192,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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xgzmz59P9+7d0x2OiEhSZXyRZe7cufTp04fCwkIldlkhFovRo0cPFi9enO5QRESSLuOTe3V1NQUFP5oVUoScnBxqamrSHYaISNJlfHIHVGKX1dLfhYhkqnaR3EVERNoTJfc27u2332azzTZb4/ZRo0Zx+eWXt2BEIiKSbi3SWt7M7gUOBea6+9bRuvWAR4H+wBTgOHcvjbb9BjgdqAV+4e6vJjOew0a/k8zD/cjz5+6e8L79+/fn7rvvZv/992/SufbYYw+++uqrJr22Md58801OPvlkpk+fnvJziYhI87RUyf3vwLAG6y4B3nD3TYA3omXMbEvgeGCr6DV/NbOsFopTRESkzWuRkru7jzWz/g1WDwf2jn6+H3gTuDha/4i7VwLfm9m3wI7Af1si1nqON/m1NXWNa4FdW1fLPffew7333stOO+3EfffeR+fOnRl922iGHRSuiRYuXMivf/VrXn/tdSoqKthzzz158ukneevNtxh56kim/DAFgIkTJ3LmGWfy7TffctBBB2Fm1HndiphefOFFfvvb3zJ1ylS22HILbv/r7QwcOBCAARsN4Oyfn80DDzzAD1N/YOjQodz793upra3loIMOorKykuLiYgC++PILpk+fzrnnnMs3X39DQUEBJ5x4AjfedGOT37d0qPM6FleqO5yIpF5BdgG5Wbktcq50DmLTw91nAbj7LDOrH0mkD/B+3H7To3U/YmZnAmcC9OvXL6nBxSfExppattoZ+Farpq6GOcvmsGD5AsZ9MI6Djz2YD779gEf+/gin//R03v3iXcyMn574UwqLC3nhvRcoLCpkwrgJTC2byuxls6nxGqaWTaWqqoojjjiCUWeN4pQzTuFfL/2L8396PmeedyZTy6byv0/+x09O/wljHh7DNoO24dnHnuXwww/ntQ9fIy8vj5q6Gv75yD+569G7yMvPY8SwEdx8582c+JMTufvxu7nwZxfy7ufvAlBNNT//xc856acnceTxR1K+tJyvJ33dqN+9NViwfAG/f/336Q5DRNqBkVuO5OCNDm6Rc7XGBnWr65+02mK0u49x98HuPrhbtx/NVd/m9F6/N8ePPJ6srCyOOuEo5s6ey/y585k7ey5v/estrv7z1XTq3ImcnBx22m2nH73+4w8/pqamhtPOOo2cnBwOGn4Q2wzaZsX2x+5/jBNGncB2g7dbcY7cvFw+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\n",
      "text/plain": [
       "<Figure size 576x432 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "plt.figure(figsize=(8,6))\n",
    "plt.stackplot(metrics6_df['airline'],\n",
    "              [metrics6_df['Incidents'], metrics6_df['Fatal_Accidents'], \n",
    "               metrics6_df['Fatalities']],\n",
    "               labels=['Incidents','Fatal_Accidents','Fatalities'],alpha=0.8)\n",
    "plt.title('Incident and Accident Comparison', color='black', fontweight = 'bold', fontsize = 12)\n",
    "plt.xlabel('Airline', color='black', fontweight = 'bold', fontsize = 12)\n",
    "plt.ylabel('Incidents by Airways', color='black', fontweight = 'bold', fontsize = 12)\n",
    "plt.xticks(rotation=60)\n",
    "plt.legend(loc=2, fontsize='large')\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
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
   "version": "3.8.5"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 4
}

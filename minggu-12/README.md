#Praktik Big Data Pertemuan 12

import pandas as pd
import numpy as np


college = pd.read_csv('data/college.csv', index_col='INSTNM')
city = college['CITY']
city.head()

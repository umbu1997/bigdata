#10 Minutes to Pandas

Impor modul modul yang dibutuhkan

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

##Pembuatan Objek
Membuat Series dengan memberikan daftar nilai, membiarkan pandas membuat indeks bilangan bulat default:

s = pd.Series([1,3,5,np.nan,6,8])
s
0    1.0
1    3.0
2    5.0
3    NaN
4    6.0
5    8.0
dtype: float64
Membuat DataFrame dengan melewatkan array NumPy, dengan indeks datetime dan kolom berlabel:

dates = pd.date_range('20130101', periods=6)
dates

df = pd.DataFrame(np.random.randn(6,4), index=dates, columns=list('ABCD'))
df
<style scoped> .dataframe tbody tr th:only-of-type { vertical-align: middle; }
.dataframe tbody tr th {
    vertical-align: top;
}

.dataframe thead th {
    text-align: right;
}
</style>
A	B	C	D
2013-01-01	0.755035	-0.484612	-0.717522	-0.687850
2013-01-02	-0.257250	-0.765153	1.093545	0.420117
2013-01-03	-0.922617	2.047103	-2.533124	0.690853
2013-01-04	0.355054	0.300695	-0.926397	1.703721
2013-01-05	-0.759857	0.366894	-1.023559	0.070350
2013-01-06	-1.370062	1.064458	0.188206	-0.977349

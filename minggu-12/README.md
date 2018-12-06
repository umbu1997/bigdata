# Praktik Big Data Pertemuan 12


```python
import pandas as pd
import numpy as np
```


```python
college = pd.read_csv('data/college.csv', index_col='INSTNM')
city = college['CITY']
city.head()
```




    INSTNM
    Alabama A & M University                   Normal
    University of Alabama at Birmingham    Birmingham
    Amridge University                     Montgomery
    University of Alabama in Huntsville    Huntsville
    Alabama State University               Montgomery
    Name: CITY, dtype: object



```python
import pandas as pd
import numpy as np
```


```python
college = pd.read_csv('data/college.csv', index_col='INSTNM')
city = college['CITY']
city.iloc[3]
```




    'Huntsville'




```python

```


```python
import pandas as pd
import numpy as np
```


```python
college = pd.read_csv('data/college.csv', index_col='INSTNM')
city = college['CITY']
city.iloc[[10,20,30]]
```




    INSTNM
    Birmingham Southern College                            Birmingham
    George C Wallace State Community College-Hanceville    Hanceville
    Judson College                                             Marion
    Name: CITY, dtype: object




```python

```


```python
import pandas as pd
import numpy as np
```


```python
college = pd.read_csv('data/college.csv', index_col='INSTNM')
city = college['CITY']
city.iloc[4:50:10]
```




    INSTNM
    Alabama State University              Montgomery
    Enterprise State Community College    Enterprise
    Heritage Christian University           Florence
    Marion Military Institute                 Marion
    Reid State Technical College           Evergreen
    Name: CITY, dtype: object




```python

```


```python
import pandas as pd
import numpy as np
```


```python
college = pd.read_csv('data/college.csv', index_col='INSTNM')
city = college['CITY']
city.loc['Heritage Christian University']
```




    'Florence'




```python

```


```python
import pandas as pd
import numpy as np
```


```python
college = pd.read_csv('data/college.csv', index_col='INSTNM')
city = college['CITY']
np.random.seed(1)
labels = list(np.random.choice(city.index, 4))
labels
```




    ['Northwest HVAC/R Training Center',
     'California State University-Dominguez Hills',
     'Lower Columbia College',
     'Southwest Acupuncture College-Boulder']




```python

```


```python
import pandas as pd
import numpy as np
```


```python
college = pd.read_csv('data/college.csv', index_col='INSTNM')
city = college['CITY']
np.random.seed(1)
labels = list(np.random.choice(city.index, 4))
city.loc[labels]
```




    INSTNM
    Northwest HVAC/R Training Center                Spokane
    California State University-Dominguez Hills      Carson
    Lower Columbia College                         Longview
    Southwest Acupuncture College-Boulder           Boulder
    Name: CITY, dtype: object




```python

```


```python
import pandas as pd
import numpy as np
```


```python
college = pd.read_csv('data/college.csv', index_col='INSTNM')
city = college['CITY']
np.random.seed(1)
labels = list(np.random.choice(city.index, 4))
city.loc['Alabama State University':'Reid State Technical College':10]
```




    INSTNM
    Alabama State University              Montgomery
    Enterprise State Community College    Enterprise
    Heritage Christian University           Florence
    Marion Military Institute                 Marion
    Reid State Technical College           Evergreen
    Name: CITY, dtype: object




```python

```



```python
import pandas as pd
import numpy as np
```


```python
college = pd.read_csv('data/college.csv', index_col='INSTNM')
city = college['CITY']
np.random.seed(1)
labels = list(np.random.choice(city.index, 4))
city.loc['Alabama State University':'Reid State Technical College':10]
```




    INSTNM
    Alabama State University              Montgomery
    Enterprise State Community College    Enterprise
    Heritage Christian University           Florence
    Marion Military Institute                 Marion
    Reid State Technical College           Evergreen
    Name: CITY, dtype: object




```python

```


## PRAKTIK BIG DATA PERTEMUAN 13

import pandas as pd
import numpy as np
state_fruit = pd.read_csv('data/state_fruit.csv', index_col=0)
state_fruit
Hasil dari source code diatas
<style scoped> .dataframe tbody tr th:only-of-type { vertical-align: middle; }
.dataframe tbody tr th {
    vertical-align: top;
}

.dataframe thead th {
    text-align: right;
}
</style>
Apple	Orange	Banana
Texas	12	10	40
Arizona	9	7	12
Florida	0	14	190
import pandas as pd
import numpy as np
state_fruit = pd.read_csv('data/state_fruit.csv', index_col=0)
state_fruit.stack()
Hasil dari source code diatas
Texas    Apple      12
         Orange     10
         Banana     40
Arizona  Apple       9
         Orange      7
         Banana     12
Florida  Apple       0
         Orange     14
         Banana    190
dtype: int64
import pandas as pd
import numpy as np
state_fruit = pd.read_csv('data/state_fruit.csv', index_col=0)
state_fruit_tidy = state_fruit.stack().reset_index()
state_fruit_tidy
Hasil dari source code diatas
<style scoped> .dataframe tbody tr th:only-of-type { vertical-align: middle; }
.dataframe tbody tr th {
    vertical-align: top;
}

.dataframe thead th {
    text-align: right;
}
</style>
level_0	level_1	0
0	Texas	Apple	12
1	Texas	Orange	10
2	Texas	Banana	40
3	Arizona	Apple	9
4	Arizona	Orange	7
5	Arizona	Banana	12
6	Florida	Apple	0
7	Florida	Orange	14
8	Florida	Banana	190
import pandas as pd
import numpy as np
state_fruit = pd.read_csv('data/state_fruit.csv', index_col=0)
state_fruit_tidy.columns = ['state', 'fruit', 'weight']
state_fruit_tidy
Hasil dari source code diatas
<style scoped> .dataframe tbody tr th:only-of-type { vertical-align: middle; }
.dataframe tbody tr th {
    vertical-align: top;
}

.dataframe thead th {
    text-align: right;
}
</style>
state	fruit	weight
0	Texas	Apple	12
1	Texas	Orange	10
2	Texas	Banana	40
3	Arizona	Apple	9
4	Arizona	Orange	7
5	Arizona	Banana	12
6	Florida	Apple	0
7	Florida	Orange	14
8	Florida	Banana	190
import pandas as pd
import numpy as np
state_fruit = pd.read_csv('data/state_fruit.csv', index_col=0)
state_fruit.stack()\
           .rename_axis(['state', 'fruit'])\
Hasil dari source code diatas
state    fruit 
Texas    Apple      12
         Orange     10
         Banana     40
Arizona  Apple       9
         Orange      7
         Banana     12
Florida  Apple       0
         Orange     14
         Banana    190
dtype: int64
import pandas as pd
import numpy as np
state_fruit = pd.read_csv('data/state_fruit.csv', index_col=0)
state_fruit.stack()\
           .rename_axis(['state', 'fruit'])\
           .reset_index(name='weight')
Hasil dari source code diatas
<style scoped> .dataframe tbody tr th:only-of-type { vertical-align: middle; }
.dataframe tbody tr th {
    vertical-align: top;
}

.dataframe thead th {
    text-align: right;
}
</style>
state	fruit	weight
0	Texas	Apple	12
1	Texas	Orange	10
2	Texas	Banana	40
3	Arizona	Apple	9
4	Arizona	Orange	7
5	Arizona	Banana	12
6	Florida	Apple	0
7	Florida	Orange	14
8	Florida	Banana	190

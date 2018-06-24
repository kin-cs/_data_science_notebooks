# data_science_notebooks

## Freq Use

## Pandas
```python
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
import seaborn as sns
import sklearn

%matplotlib inline

pd.options.display.max_columns = 999  # VERY IMPORTANT!!!

from IPython.core.interactiveshell import InteractiveShell
InteractiveShell.ast_node_interactivity = "all"

# using .eq('something')
df[df['col_A'].eq('some_term')]

# using .quary('some quary')
df.query("col_A == 'some_term'")

# using .isin( a_list )
df['col_A'].isin(a_list_of_terms)

# using 'hello'.replace('o','a')  # replacing the string of o with a

# using 'hello2222'.strip('2')  # return 'hello'

# using in print() function, using argument file=file_object to write in a file

# checking NaN and return Boolean
df['col_A'].isnull() 

# making bins columns
age_bins = np.arange(0, 80, 5)
pd.cut(df['col_age'], age_bins, right=False)

# unpacked multi items when using apply
df[['sum', 'difference']] = df.apply(lambda row: pd.Series(add_subtract(row['a'], row['b'])), axis=1)

# rolling avg based on the previous data
# https://stackoverflow.com/questions/28642511/how-to-apply-rolling-functions-in-a-group-by-object-in-pandas
  df.index = [pd.to_datetime(str(x), format='%Y%m%d') for x in df.index]
  df.reset_index(inplace=True)
  def avg_3_days(x):
          return df[(df['index'] >= x['index'] - pd.DateOffset(3)) & (df['index'] < x['index']) & (df['fruit'] == x['fruit'])].amount.mean()

  df['res'] = df.apply(avg_3_days, axis=1)
  df
  ==result==
         index   fruit  amount  res
  0 2014-01-01   apple       3  NaN
  1 2014-01-02   apple       5    3
  2 2014-01-02  orange      10  NaN
  3 2014-01-04  banana       2  NaN
  4 2014-01-04   apple      10    4
  5 2014-01-04  orange       4   10
  6 2014-01-05  orange       6    7
  7 2014-01-05   grape       1  NaN

```

# Kaggle
### Kernel Ref.

- U-nets: https://www.kaggle.com/lscoelho/keras-u-net-lb-0-277-epochs-vsplit-thr

## Avito

### LightGBM hyper-parameter tuning
- Optimization software: Hyperopt, scikit-optimize, spearmint...
- num_leaves: more powerful it is
- bagging_fraction: just take part of the batch data to train
- min_data_in_leaf: another regularization, quite good to enlarge it to regularization for avoiding overfitting
- feature_fraction: just like dropout, very useful to set it like 0.5 (just like ensemble method)

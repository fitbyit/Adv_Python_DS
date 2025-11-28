```
import pandas as pd
import numpy as np

# Possible categories
regions = ['North', 'South', 'East', 'West']
products = ['A', 'B', 'C']

# Generate random dataset
np.random.seed(42)  # optional (for reproducible results)

df = pd.DataFrame({
    'Region': np.random.choice(regions, size=10),
    'Product': np.random.choice(products, size=10),
    'Sales': np.random.randint(500, 3000, size=10)   # random sales between 500–3000
})

print(df)

```

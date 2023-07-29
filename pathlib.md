Neat way to write file paths:

```python
import pandas as pd
from pathlib import Path

dataset_path = Path("datasets")
filename = "data.csv"

pd.read_csv(dataset_path / filename)
```

[[python]]
---
{
  "title": "Test Notebook",
  "subtitle": "Generic subtitle",
  "date": "2017-12-03",
  "slug": "test-notebook"
}
---
<!--more-->

### Test of Jupyter notebook with Hugo


```python
import numpy as np
import matplotlib.pyplot as plt

%matplotlib inline
```

```python
y = np.random.normal(size=100)
```

```python
plt.figure(figsize=(15, 8))
plt.plot(y)
plt.title("A Very Pretty Graph")
plt.show()
```

![png](output_3_0.png)


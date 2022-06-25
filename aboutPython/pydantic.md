`python`

> [pydantic](https://pydantic-docs.helpmanual.io/)

#### BaseModel
```python
from pydantic import BaseModel
from typing import Dict, Tuple

class BaseModelDemo(BaseModel):
    a : int = 0
    b : str = "aaa"
    c : Dict[str,int] = {"aaa": b}
    d : Tuple[int,str,float] = (1, "xxx", 1.23)
demo = BaseModelDemo()
print(demo.json())
```

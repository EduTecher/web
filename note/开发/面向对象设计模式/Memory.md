```python
# Singleton
class Singleton:
    def __init__(self):
        pass
    def do(self):
        pass
instance = Singleton()
del Singleton
```



```python
# Prototype
class Prototype:
    def __init__(self):
        pass
    def do(self):
        pass
    def clone(self):
        return self.__class__(**self.__dict__)
        
instance_prototype = Prototype()
del Prototype
instance_2 = instance_prototype.clone()
```



```python
# Pool

# Thread Pool
from concurrent.futures import ThreadPoolExecutor
ThreadPoolExecutor()

# Process Pool
multiprocessing.Pool()
```




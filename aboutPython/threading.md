### python 多线程
#### demo
```python
import threading、
def func(i):
    print(i)
    print(threading.current_thread().name)  ## test_func

t1 = threading.Thread(target=func,name='test_func',args=(1,))
t1.start()
t1.join()  #阻塞主进程
```
#### 线程池
```python
from concurrent.futures import ThreadPoolExecutor


def func(i):
    print(i)
    print(threading.current_thread().name)  ## test_func_*

with ThreadPoolExecutor(max_worker=4, thread_name_prefix='test_func') as pools:
    for i in range(100):
        pools.submit(get_data, i)
```

#### 内存泄漏
线程池默认使用无界队列，在IO密集型应用中，如果待处理数据过多，会导致线程池中待处理线程增长过快，如果不加以限制，则会出现内存泄漏.

```python
import time
from concurrent.futures import ThreadPoolExecutor


def func(i):
    time.sleep(100)
    print(i)
    print(threading.current_thread().name)  ## test_func_*

# 默认最大工作线程为4，每个线程休眠100秒
# 但是全部任务数量为100000个，此时所有任务都会在线程池中排队
with ThreadPoolExecutor(max_worker=4, thread_name_prefix='test_func') as pools:
    for i in range(100000):
        pools.submit(get_data, i)
```

解决办法: 限制线程池队列长度
```python
class BoundedThreadPoolExecutor(ThreadPoolExecutor):
    def __init__(self, max_workers=None, thread_name_prefix=''):
        super().__init__(max_workers, thread_name_prefix)
        self._work_queue = Queue(self._max_workers*2) # 队列长度为工作线程的两倍
```
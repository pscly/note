# ddt

## 作用

我个人理解的是，他就是给unittest 穿参数的东西

```python
from ddt import ddt, unpack

# test_f1是unittest子类的函数
# 他在这里就会给aa传参, 因为ddt里面有两个参数，所以会执行两次f1这个实例

@ddt('11','22')
def test_f1(self, aa):
    pass


# 如果有两个参数的话，就需要加个括号， 这样就会当成一个整体
# 可以使用unpack 进行解开， 这样就是多个参数了
@ddt(['11','22'])
@unpack
def test_f2(self, aa, bb):
    pass

```

## 导入文件的数据

> abc.yaml里面放到是字典, aa,bb是键值对

```python
from ddt import file_data

@file_data('./abc.yaml')
def test_f2(self, aa, bb):
    pass

# 建议用这个，别写死了 
@file_data('./abc.yaml')
def test_f2(self, **kwargs):
    pass


```

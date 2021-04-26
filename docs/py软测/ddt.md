# ddt

## 作用

我个人理解的是，他就是给unittest 穿参数的东西

```python
# coding: utf-8

import unittest
from ddt import ddt, unpack, file_data, data

# 使用unittest和ddt 
@ddt
class Cases(unittest.TestCase):

    # 使用ddt
    @data('123')
    def test_01(self, *args):
        print('01>>', args)
        # self.tearDown()


if __name__ == '__main__':
    unittest.main()


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

# 简介UnitTest

> 在python中 测试的框架(unittest, pytest)

- [简介UnitTest](#简介unittest)
  - [四大特性](#四大特性)
  - [其他](#其他)
  - [前置和后置](#前置和后置)

## 四大特性

1. 可以实现selenium,appium, requests接口自动化
2. 可以关于测试用例基于TestCase类来实现
3. 测试套件与运行器，可以精细化管理测试用例以及生成测试报告
4. 断言机制, 可以直接通过self.来调用已经封装好的所有断言函数(满足很多需求，不用自己在写了)

## 其他

1. 它默认就装在了我们的python中
2. 定义用例的函数必须是 test_ 开头的 才会被识别为测试用例, 会自动运行用例
   1. 运行用例的 运行顺序是 0-9  A-Z  a-z
3. unittest的执行，必须是mian函数中, 调用UnitTest.main()来执行

## 前置和后置

如果是退出一类的方法，可以放到后置里面，但是如果是sleep这种方法，不太建议，因为后置已经是要退出的状态了

> 每一条命令执行时，都会执行前置和后置

```python
# 调用unittest
class Cases(unittest.TestCase):

    def setUp(self) -> None:
        print('这里是前置')

    def tearDown(self) -> None:
        print('这里是后置')

    def test_01(self):
        print('01')
        # self.tearDown()

    def test_03(self):
        print('03')

    def test_02(self):
        print('02')

```

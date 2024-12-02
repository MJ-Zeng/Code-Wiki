# **<font style="color:#ECAA04;">一</font>**<font style="color:#ECAA04;">、</font>**<font style="color:#ECAA04;">if语句的定义</font>**
在 Python 中，if语句是一种<font style="color:#DF2A3F;">控制结构</font>，用于根据某个条件的值决定是否执行特定的代码块。if语句的作用就是根据<font style="color:#DF2A3F;">一个或多个条件对代码进行分支控制</font>。

## **<font style="color:#ECAA04;">二</font>**<font style="color:#ECAA04;">、</font>**<font style="color:#ECAA04;">if语句的格式分类</font>**
在 Python 中，if语句有三种基本格式：

## 1.<font style="color:#DF2A3F;">i</font>**<font style="color:#DF2A3F;">f语句</font>**的格式如下：
```python
if 条件:    #格式：if 条件 :（冒号）
    # 当条件成立时执行这里的代码块

```

如果条件成立，则执行if语句后面的代码块；否则不执行。

```python
score= int(input("请输入一个数字："))
if score >90:
    print("优秀")
```

## 2**.****<font style="color:#DF2A3F;">if-else语句</font>**
if-else 语句的格式如下

```python
f 条件:    
    # 当条件成立时执行这里的代码块
else:
    # 当条件不成立时执行这里的代码块
```

如果条件成立，则执行冒号后面的代码块；否则，执行else语句后面的代码块

```python
num = int(input("请输入一个数字：")
if num % 2 == 0:
          print(num,"是偶数")
else:
    print(num,"是奇数")
```

## 3.**<font style="color:#DF2A3F;">if-elif-else语句</font>**
```python
if 条件1:
    # 当条件1成立时执行这里的代码块
elif 条件2:
    # 当条件2成立时执行这里的代码块
elif 条件3:
    # 当条件3成立时执行这里的代码块
else:
    # 当以上条件都不成立时执行这里的代码块
```

根据条件的不同结果，执行相应的代码块。如果条件1成立，则执行if语句后面的代码块；如果条件1不成立而条件2成立，则执行第二个elif语句后面的代码块；以此类推，如果所有条件都不成立，则执行else语句后面的代码块。

```python
'''在现实世界中,很多情况下需要考虑的情形都超过两个。例如如,来看一个根据年龄段收费的游乐场:
4岁以下免费;
4~18岁收费5美元;
18岁(含)以上收费10美元'''
 
age=int(input("请输入你的年龄:"))
if age < 4:
    print("免费")
elif age >= 4 and age < 18 :
    print("收费5美元")
else:
    print("收费10美元")
```



### **<font style="color:#ECAA04;">三、if语句的条件表达式</font>**
在 Python 中，<font style="color:#F8B881;">if语句可以使用以下条件表达式：</font>

<font style="color:#1DC0C9;">比较运算符：==（等于）、!=（不等于）、>（大于）、<（小于）、>=（大于等于）、<=（小于等于）</font>

<font style="color:#1DC0C9;">逻辑运算符：and（与）、or（或）、not（非）</font>

<font style="color:#1DC0C9;">成员运算符：in、not in</font>

<font style="color:#1DC0C9;">身份运算符：is、is not</font>

这些条件可以组合使用，构成一个复杂的条件表达式。



#### **<font style="color:#ECAA04;">四、使用if语句的注意事项</font>**
判断条件必须是**<font style="color:#F8B881;">布尔型</font>**<font style="color:#F8B881;"></font>

1.if语句后面的判断条件必须是<font style="color:#DF2A3F;">布尔型</font>，即<font style="color:#2F8EF4;">True</font>或<font style="color:#2F8EF4;">False</font>。如果条件表达式不是布尔型，在执行时Python会将其转换为布尔值再进行判断。<font style="color:#2F8EF4;">对于0、空字符串、空列表、空字典等“空”值，Python会将其转换为False</font>；而<font style="color:#2F8EF4;">非零数值、非空字符串、非空列表、非空字典等“非空”值则会被转换为True。</font>

使用缩进来表示层次关系

2.Python中<font style="color:#DF2A3F;">没有大括号{}来表示代码块</font>，而是通过<font style="color:#DF2A3F;">缩进</font>来表示代码块的层次关系。同一个代码块中的所有语句必须保持相同的缩进，通常使用<font style="color:#DF2A3F;">4个空格</font>作为标准缩进。

3.if语句可以与<font style="color:#ECAA04;">else语句</font>搭配使用

4.if语句可以搭配else语句使用，当if语句的条件不成立时，就会执行else语句中的代码。例如：

5.if语句可以<font style="color:#ECAA04;">嵌套</font>使用

6.if语句也可以嵌套使用，当一个条件成立后，还需要进一步判断时，就可以使用if的嵌套形式。

7.两个条件相同时，只运行第一个

```python
age=int(input("请输入年龄:"))
if age >18:
    print("你可以自由进入网吧")
elif 16<=age <= 18:
    print("可以在家长的监督下进入网吧")                  #16岁重复了
elif 14<= age<= 16:
    print("可以在家长的监督下进入网吧,最多呆半个小时")      #16岁重复了
else:
    print("未成年禁止进入")
```

以上例子，有两个16岁的条件，只运行了第一个



##### **<font style="color:#ED740C;">五、if语句的常用操作</font>**
##### 1.判断数值大小
```python
# 判断一个变量num是否大于等于10
num=int(input("请输入一个数字:"))
 
if num >= 10:
    print("num大于等于10")
else:
    print("num小于10")
```

##### 2.判断字符串
```python
#判断一个字符串str是否等于"清微"
name=input("请输入一个名称:")
if name == "清微":
    print("名称叫清微")
else:
    print("名字不叫清微")
```

##### 3.判断逻辑表达式
例如，判断两个变量是否都为真。

```python
'''如果用户输入了正确的用户名adaim以及对应的正确密码123456,就显示
"登录成功",若用户名或者密码有一个错了,都显示"用户名或密码错误"'''
 
username=input("请输入账号:")
password=input("请输入密码:")
if username=="admin" and password=="123456":
    print("登录成功")
else:
    print("用户名和密码错误")
```

##### 4.使用elif
```python
'''如果用户输入了正确的账号adaim和对应的正确密码123456,就显示"登录成功",
若用户名输入错误显示"账号错误",若密码错误则显示"密码错误",若账号和密码都错
误显示"账号和密码错误"'''
username=input("请输入账号:")
password=input("请输入密码:")
if username=="admin"and password=="123456":
    print("登录成功")
elif username!="admin"and password=="123456":
    print("账号错误")
elif username == "admin" and password != "123456":
    print("密码错误")
else:
    print("用户名和密码错误")
```

##### 5.嵌套if语句
```python
score = int(input("请输入考试成绩："))
 
if score >= 90:
    print("优秀")
else:
    if score >= 80:
        print("良好")
    else:
        if score >= 70:
            print("中等")
        else:
            if score >= 60:
                print("及格")
            else:
                print("不及格")
```


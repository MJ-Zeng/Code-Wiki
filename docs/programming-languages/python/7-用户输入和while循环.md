# 7.1.1 input()函数的工作原理
## input()函数
在Python中，input() 函数用于从<font style="color:#ED740C;">标准输入</font>（通常是用户的键盘）读取<font style="color:#ED740C;">一行文本</font>，并以字符串的形式返回。如果用户输入了一些内容并按下了回车键，input() 就会返回用户输入的内容。如果没有输入任何内容直接按下回车键，则返回一个空字符串。

简单用法示例如下

```abap
user_input = input("请输入一些文本: ")
print("您输入的是:", user_input)
```

## 7.1.2 使用int()来获取数值输入
1. input()函数会把控制台输入的数字解读成<font style="color:#DF2A3F;">字符串</font>，此时我们徐要借助<font style="color:#DF2A3F;">int()函数</font>来将其转换成数值

```abap
user_input = input("请输入你的年龄: ")

age = int(user_input)

if age >= 18:
    print("你已成年")
if age >= 65:
    print("你已经是老人了")
else:
    print("你还是年轻")


```

## 7.1.3求模运算符
2. 求模运算符是把<font style="color:#DF2A3F;">两数相除</font>，<font style="color:#DF2A3F;">取余</font>的过程。这里笔者同时展示下/除法运算符，代码如下

```abap
print(7/3)
print(7%3)
```



## 7.2while循环简介
### 7.2.1使用while循环
1. 简单的while循环，打印数字，从1到5

```abap
current_number = 1
while current_number <= 5:
    print(current_number)
    current_number+= 1

```

### 7.2.2让用户选择何时退出
```abap
prompt = "\nTell me something,and I will repeat it back to you:"
prompt+= "\nEnter 'quit' to end the program."
message = ""
while message != 'quit':
    message = input(prompt)
    if message == 'quit':
        break
    print(message)
```

### 7.2.3使用标签
当我们的代码需要判断多个不同的条件是否进入循环时，我们需要一个统一的<font style="color:#DF2A3F;">标志</font>

```abap
# 初始化标志变量
continue_loop = True

while continue_loop:
    # 获取用户输入
    user_input = input("请输入一个数字: ")

    # 使用 if 条件判断用户输入的数字
    if int(user_input) > 10:
        print("你输入的数字大于 10!")
    elif int(user_input) == 10:
        print("你输入的数字等于 10!")
    else:
        print("你输入的数字小于或等于 10!")

    # 决定是否继续循环
    continue_input = input("你想继续吗？(y/n): ")
    if continue_input.lower() != 'y':
        continue_loop = False

print("循环结束")

```

### 7.2.4使用break退出循环
对上面的代码简单修改，不使用标志，while循环条件始终为True。循环内部判断是否跳出循环，使用<font style="color:#DF2A3F;">关键字</font>

```abap
while True:
    # 获取用户输入
    user_input = input("请输入一个数字: ")

    # 使用 if 条件判断用户输入的数字
    if int(user_input) > 10:
        print("你输入的数字大于 10!")
    elif int(user_input) == 10:
        print("你输入的数字等于 10!")
    else:
        print("你输入的数字小于或等于 10!")

    # 决定是否继续循环
    continue_input = input("你想继续吗？(y/n): ")
    if continue_input.lower() != 'y':
       break

print("循环结束")
```

### 7.2.5在循环中使用continue
continue和break是有区别的，continue是<font style="color:#DF2A3F;">不继续执行</font>当前循环代码，直接进入<font style="color:#DF2A3F;">下一次循环</font>

```abap
current_number = 0
while current_number <10:
    current_number+= 1
    if current_number % 2 == 0:
        continue
    print(current_number)
```



### 7.3使用while循环来处理列表和字典
#### 7.3.1在列表之间移动元素
for循环是一种<font style="color:#DF2A3F;">遍历列表</font>的有效方式，但是不应该在for循环中<font style="color:#DF2A3F;">修改列表</font>。我们应该使用while循环来遍历并修改列表。

```abap
# 首先，创建一个待验证用户列表
# 和一个用于存储已验证用户的空列表
unconfirmed_users = ['alice', 'brian', 'candace']
confirmed_users = []
# 验证每个用户，直到没有未验证用户为止
#  将每个经过验证的列表都移到已验证用户列表中
while unconfirmed_users:
    current_user = unconfirmed_users.pop()
    print("Verifying user:" + current_user.title())
    confirmed_users.append(current_user)
# 显示所有已验证的用户
print("\nThe following users have been confirmed:")
for confirmed_user in confirmed_users:
    print(confirmed_user.title())
```

#### 7.3.2删除包含特定值的所有列表元素
前面说过，删除列表中的特定值，使用<font style="color:#DF2A3F;">remove</font>就可以，但是remove只会删除第一个，特定值有多个怎么删除？答案是借助<font style="color:#DF2A3F;">while循环</font>

```abap
languages = ["Java", "Python", "C++", "JavaScript", "Ruby", "Java"]

while "Java" in languages:
    languages.remove("Java")

print(languages)
```

#### 7.3.3使用用户输入来填充字典
下面来创建一个调查程序，其中的循环每次执行时都提示输入被调查者的名字和回答。我们将收集的数据存储在一个字典中，以便将回答同被调查者关联起来

```abap
responses = {}  # 初始化一个空字典

# 设置一个标志，用于控制循环何时停止
polling_active = True

while polling_active:
    # 提示用户输入信息
    name = input("\n您的名字是什么？ ")
    language = input("您喜欢哪种编程语言？ ")

    # 存储响应
    responses[name] = language

    # 看看是否还有其他人参与调查
    repeat = input("您想让其他人也参与回答吗？(是/否) ")
    if repeat == '否':
        polling_active = False

# 调查结束，显示结果
print("\n--- 调查结果 ---")
for name, language in responses.items():
    print(f"{name} 喜欢 {language}。")
```

#### 总结
通过本文，我们学会了如何在程序中使用input()来让用户提供信息；如何处理文本和数字输入，以及如何使用while循环让程序按用户的要求不断地运行；多种控制while循环流程的方式：设置活动标志、使用break语句以及使用continue语句；如何使用while循环在列表之间移动元素，以及如何从列表中删除所有包含特定值的元素；如何结合使用while循环和字典。

对于文中的代码示例，我们应该多加练习才能掌握。


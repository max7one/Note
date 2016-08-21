## 基本语法

print("Hello World！")  
输出 -- 没有分号结尾



用 2 个方括号 "[[]]" 来表示"一块"字符串
```
html = [[
<html>
<head></head>
<body>
    <a href="http://www.w3cschool.cc/">w3cschool菜鸟教程</a>
</body>
</html>
]]
print(html)
```
Lua 里表的默认初始索引一般以 1 开始


单行注释
```
--
```
多行注释
```
--[[
 多行注释
 多行注释
--]]
```

#### 变量

编译程序执行代码之前编译器需要知道如何给语句变量开辟存储区，用于存储变量的值。

Lua 变量有3种类型
- 全局变量(没有关键词)
- 局部变量(关键词 local)
- 表中的域  

Lua 中的变量全是全局变量，那怕是语句块或是函数里，除非用 local 显示声明为局部变量。

局部变量的作用域为从声明位置开始到所在**语句块**结束。
变量的默认值均为`nil`



##  数据类型

#### 1. table

`table`  是一个"关联数组"（associative arrays），数组的索引可以是数字或者是字符串  
    不同于其他语言的数组把 0 作为数组的初始索引

在 Lua 里表的 **默认初始索引一般以 1 开始**

构造一个初始表
```
local tbl2 = {"apple", "pear", "orange", "grape"}
```

遍历表
```
local tb = {"apple", "pear", "orange", "grape"}
for k, v in pairs(tb) do
    print(k .. " : " .. v)
end
```

## 函数

```
function func(n)
    print ("hello")
end
```

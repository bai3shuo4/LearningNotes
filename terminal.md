Terminal Command
===
1. Ctrl+Alt+T 打开终端
2. 一些常用的终端快捷键:
3. Ctrl+L 清空屏幕(功能相当于命令clear)
4. Ctrl+U 剪切文本直到行的起始(可以用于清空行)
5. Ctrl+K 剪切文本直到行的末尾
6. Ctrl+Y 粘贴最近剪切的文本
7. Ctrl+C 杀死当前进程(也可以用来清空当前行)
8. Ctrl+D 退出当前Shell(功能相当于命令exit) 或者 删除当前的字符
9. Ctrl+A 行首
10. Ctrl+E 行尾
11. Home/End 行首/行尾
12. Ctrl+F 向前移动一个字符
13. Ctrl+B 向后移动一个字符
14. Ctrl+P 或 Ctrl+N 上下历史记录
15. 上下方向键 上下历史记录
16. Ctrl+Shift+C 复制
17. Ctrl+Shift+V 粘贴
18. 还有Tab补全,按住Ctrl键进行块选择.
19. 鼠标中键:粘贴(在gnome-terminal中使用"菜单键+P"也是可以粘贴的)

Bash Sign
===

\#
---
comment, use \ as meaning transfer

;
---
write one or more commands in one line

;;
---
end case. e.g

```
 #!/bin/bash
 varname=b
 case "$varname" in
     [a-z]) echo "abc";;
     [0-9]) echo "123";;
 esac
```

.
---
equal to source

' or "
---
stop interpretting special sign in string

`
---
allow an output of a command to give its value to another value. e.g

```
caffemodel = `basename \path\to\caffemodel`
```

:
---
NOP

\>
---
clear a file without changing its authorize

\>>
---
no change to previous existed file

:
---
split sign for values

$
---
transform of value. e.g

```
#!/bin/bash

var1=5
var2=23skidoo

echo $var1     # 5
echo $var2     # 23skidoo
```

equal to ``

()
---
1. as a sub shell
2. init array

{}
---
expand file name. e.g

```
{a,b}.txt -> a.txt b.txt
a.{txt,exe} -> a.txt a.exe
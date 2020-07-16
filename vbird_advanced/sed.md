`sed`命令可以对数据进行取代、删除、新增特定行等等的功能

1. sed [-nefr] [动作] 

-n ：只有经过sed处理过的行才会被显示出来。
-e ：直接在指令列模式上进行sed的动作编辑
-f ：直接将sed的动作写在一个文件内
-i ：直接修改读取的文件内容，而不是由屏幕输出

动作有如下这些：  
a：新增行，例如动作为`2a  haha`，则第二行后新增一行，内容为haha  
c：取代行，例如动作为`2,10c replace`,则二到十行的内容被替换为replace字符串  
d：删除行，例如动作为`2,10d`, 则删除二到十行。  
i：插入行，属于头插，例如动作为`2i 666`，则在原本第二行之前插入行555  
p：打印，亦将某个选择的数据打印出来，通常与`-n`选项一起使用  
s：取代，真正的对行的内容进行替换，可以搭配正则表达式对内容进行搜索替换，例如`'s/old/new/g'`，将所有行的所有的old替换为new。

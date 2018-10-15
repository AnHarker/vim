# vim
##vim
#### 命令模式
>-  ZZ保存退出
- ZQ不保存退出

>命令模式= =  = =       ===>插入模式
>- i insert, 在光标所在处输入
- I在当前光标所在行的行首输入
- aappend, 在光标所在处后面输入
- A在当前光标所在行的行尾输入
- o在当前光标所在行的下方打开一个新行
- O在当前光标所在行的上方打开一个新行

>光标移动
- 字符间跳转：
&emsp;h: 左l: 右j: 下k: 上
&emsp;\#COMMAND：跳转由#指定的个数的字符
- 单词间跳转：
&emsp;w：下一个单词的词首
&emsp;e：当前或下一单词的词尾
&emsp;b：当前或前一个单词的词首
&emsp;\#COMMAND：由#指定一次跳转的单词数
- 当前页跳转：
&emsp;H：页首M：页中间行L:页底
&emsp;zt：将光标所在当前行移到屏幕顶端
&emsp;zz：将光标所在当前行移到屏幕中间
&emsp;zb：将光标所在当前行移到屏幕底端
- 行首行尾跳转：
&emsp;^: 跳转至行首的第一个非空白字符
&emsp;0: 跳转至行首
&emsp;$: 跳转至行尾
- 行间移动：
&emsp;\#G、扩展命令模式下：# 跳转至由#指定行
&emsp;G：最后一行
&emsp;1G, gg: 第一行
- 句间移动：
&emsp;)：下一句(：上一句
- 段落间移动：
&emsp;}:下一段{：上一段
- Ctrl+f: 向文件尾部翻一屏
- Ctrl+b: 向文件首部翻一屏
- Ctrl+d: 向文件尾部翻半屏
- Ctrl+u：向文件首部翻半屏

>字符编辑：
- &emsp;x: 删除光标处的字符
&emsp;\#x: 删除光标处起始的#个字符
&emsp;xp: 交换光标所在处的字符及其后面字符的位置
&emsp;~:转换大小写
&emsp;J:删除当前行后的换行符
- 替换命令(r, replace)
&emsp;r: 替换光标所在处的字符
&emsp;R:切换成REPLACE模式
- 删除命令：
&emsp;d: 删除命令，可结合光标跳转字符，实现范围删除
&emsp;d$: 删除到行尾
&emsp;d^:删除到非空行首
&emsp;d0:删除到行首
&emsp;dw:
&emsp;de:
&emsp;db:
&emsp;#COMMAND
- dd: 删除光标所在的行
&emsp;#dd：多行删除
- D：从当前光标位置一直删除到行尾，等同于d$
- 复制命令(y, yank)：
&emsp;y: 复制，行为相似于d命令
&emsp;y$
&emsp;y0
&emsp;y^
&emsp;ye
&emsp;yw
&emsp;yb
&emsp;#COMMAND
- yy：复制行
&emsp;#yy: 复制多行
- Y: 复制整行
- 粘贴命令(p, paste)：
&emsp;p：缓冲区存的如果为整行，则粘贴当前光标所在行的下方；否则，则粘贴至当前光标所在处的后面
&emsp;P：缓冲区存的如果为整行，则粘贴当前光标所在行的上方；否则，则粘贴至当前光标所在处的前面
- 改变命令(c, change)
&emsp;c: 修改后切换成插入模式
- 命令模式--> 插入模式
&emsp;c$
&emsp;c^
&emsp;c0
&emsp;cb
&emsp;ce
&emsp;cw
&emsp;#COMMAND
- cc：删除当前行并输入新内容，相当于S
&emsp;#cc
- C：删除当前光标到行尾，并切换成插入模式

> - 100iwang [ESC] 粘贴“wang”100次
- < start position>&emsp;< command >&emsp;< end position >
&emsp;Command:
&emsp;&emsp;y 复制、d 删除、gU变大写、gu变小写
&emsp;例如0y\$ 命令意味着：
&emsp;&emsp;0 → 先到行头
&emsp;&emsp;y → 从这里开始拷贝
&emsp;&emsp;$ → 拷贝到本行最后一个字符
&emsp;&emsp;ye 从当前位置拷贝到本单词的最后一个字符
- di" 光标在""之间，则删除""之间的内容
- yi( 光标在()之间，则复制()之间的内容
- vi[ 光标在[]之间，则选中[]之间的内容
- dtx删除字符直到遇见光标之后的第一个x 字符
- ytx复制字符直到遇见光标之后的第一个x 字符

> - u撤销最近的更改
- #u撤销之前多次更改
- U撤消光标落在这行后所有此行的更改
- 按Ctrl-r重做最后的“撤消”更改
- . 重复前一个操作
- n.重复前一个操作n次

###扩展命令模式
>扩展命令模式：(使用 **:** 进入命令模式)
- 命令：
&emsp;w写（存）磁盘文件
&emsp;wq写入并退出
&emsp;x写入并退出
&emsp;q 退出
&emsp;q！不存盘退出，即使更改都将丢失
&emsp;r filename读文件内容到当前文件中
&emsp;w filename将当前文件内容写入另一个文件
&emsp;!command执行命令
&emsp;r!command读入命令的输出

> ####地址定界
- :start_pos,end_pos
- # 具体第#行，例如2表示第2行
- #,# 从左侧#表示起始行，到右侧#表示结尾行
- #,+# 从左侧#表示的起始行，加上右侧#表示的行数
&emsp;：2,+3 表示2到5行
- . 当前行
- \$ 最后一行
&emsp;.,\$-1 当前行到倒数第二行
- % 全文, 相当于1,$
- /pat1/,/pat2/
&emsp;从第一次被pat1模式匹配到的行开始，一直到第一次被pat2匹配到的行结束
&emsp;#,/pat/
&emsp;/pat/,$
- 使用方式：后跟一个编辑命令
&emsp;d
&emsp;y
&emsp;w file: 将范围内的行另存至指定文件中
&emsp;r file：在指定位置插入指定文件中的所有内容
- 查找
&emsp;/PATTERN：从当前光标所在处向文件尾部查找
&emsp;?PATTERN：从当前光标所在处向文件首部查找
&emsp;n：与命令同方向
&emsp;N：与命令反方向
- s: 在扩展模式下完成查找替换操作
&emsp;格式：s/要查找的内容/替换为的内容/修饰符
&emsp;要查找的内容：可使用模式
&emsp;替换为的内容：不能使用模式，但可以使用\1, \2, ...等后向引用符号；还可以使用“&”引用前面查找时查找到的整个内容
&emsp;修饰符：
&emsp;i: 忽略大小写
&emsp;g: 全局替换；默认情况下，每一行只替换第一次出现
&emsp;gc:全局替换，每次替换前询问
- 查找替换中的分隔符/可替换为其它字符，例如
&emsp;s@/etc@/var@g
&emsp;s#/boot#/#i

####寄存器
> - 有26个命名寄存器和1个无命名寄存器，常存放不同的剪贴版内容，可以不同会话间共享
- 寄存器名称a，b,…,z,格式：“寄存器放在数字和命令之间
如：3"tyy 表示复制3行到t寄存器中
"tp表示将t寄存器内容粘贴
- 未指定，将使用无命名寄存器
- 有10个数字寄存器，用0，1，…，9表示，0存放最近复制内容，1存放最近删除内容。当新的文本变更和删除时，1转存到2，2转存到3，以此类推。数字寄存器不能在不同会话间共享
###标记和宏
>- ma 将当前位置标记为a，26个字母均可做标记，mb、mc 等等；
- 'a 跳转到a标记的位置；实用的文档内标记方法，文档中跳跃编辑时很有用
- qa录制宏a，a为宏的名称
- q 停止录制宏，
- @a 执行宏a
- @@ 重新执行上次执行的宏
###编辑二进制文件
>- 以二进制方式打开文件
vim –b binaryfile
- 扩展命令模式下，利用xxd命令转换为可读的十六进制
:%!xxd
- 编辑二进制文件
- 扩展命令模式下，利用xxd命令转换回二进制
:%!xxd–r
- 保存退出
###可视化模式
>- 允许选择的文本块
&emsp;v面向字符
&emsp;V面向行
&emsp;ctrl-v 面向块
- 可视化键可用于与移动键结合使用：
&emsp;w)}箭头等
- 突出显示的文字可被删除，复制，变更，过滤，搜索，替换等
###多文件模式
>- vim FILE1 FILE2 FILE3 ...
:next 下一个
:prev前一个
:first 第一个
:last 最后一个
:wall 保存所有
:qall退出所有
:wqall
###使用多个"窗口"
>- 多文件分割
&emsp;vim -o|-O FILE1 FILE2 ...
&emsp;-o: 水平分割
&emsp;-O: 垂直分割
&emsp;在窗口间切换：Ctrl+w, Arrow
- 单文件窗口分割：
&emsp;Ctrl+w,s: split, 水平分割
&emsp;Ctrl+w,v: vertical, 垂直分割
&emsp;ctrl+w,q：取消相邻窗口
&emsp;ctrl+w,o:取消全部窗口
&emsp;：wqall退出
###工作特性
>- 配置文件：永久有效
&emsp;全局：/etc/vimrc
&emsp;个人：~/.vimrc
- 扩展模式：当前vim进程有效
- 行号
&emsp;显示：set number, 简写为set nu
&emsp;取消显示：set nonumber, 简写为set nonu
- 忽略字符的大小写
&emsp;启用：set ic
&emsp;不忽略：set noic
- 自动缩进
&emsp;启用：set ai
&emsp;禁用：set noai
- 智能缩进
&emsp;启用：smartindent简写set si
&emsp;禁用：set nosi
- 高亮搜索
&emsp;启用：set hlsearch
&emsp;禁用：set nohlsearch
- 语法高亮
&emsp;启用：syntax on
&emsp;禁用：syntax off
- 显示Tab和换行符^I 和$显示
&emsp;启用：set list
&emsp;禁用：set nolist
- 文件格式
&emsp;启用windows格式：set fileformat=dos
&emsp;启用unix格式：set fileformat=unix
&emsp;简写：set ff=dos|unix
- 设置文本宽度
&emsp;set textwidth=65 (vimonly)
&emsp;set wrapmargin=15
- 设置光标所在行的标识线
&emsp;启用：set cursorline，简写cul
&emsp;禁用：set no cursorline
- 复制保留格式
&emsp;启用：set paste
&emsp;禁用：set nopaste

 **解决删除文件或文件夹时提示“找不到该项目 该项目不在......中，请确认该项目的位置，然后重试。……”**  
   在今天编辑周报时遇到的错误，经过查阅资料完成解决。  
   出现此问题的原因:  

   一、文件或文件夹名称不符合Windows命名规范;比如名称中含有..等特殊符号;  

   二、使用下载工具创建的文件夹,在未下载完成前自行删除文件  

   三、系统备份文件GHOST创建的文件(我是系统备份的ghost产生的,装双系统时  

   四、恶意文件生成的防删除目录。  

新建文件文本,是txt格式的那种

把以下代码复制粘贴到一新建的txt记事本文档中，并另存为1.bat文件（或者你喜欢的名字），注意扩展名为批处理文件bat；

从下面加粗的黑体字开始复制：

DEL /F /A /Q \\?\%1

RD /S /Q \\?\%1


把要删除的出错文件夹拖入.bat窗口，就可以删除了。

PS:最开始试图删除单个文件没有成功，但尝试了几次删除文件夹就成功了。
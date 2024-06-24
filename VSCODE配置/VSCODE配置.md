<b><div align='center' ><font size='5'>搜索并且下载VSCode</font></div></b>


[虽然你可以搜索但是为了省事，但我推荐你培养一下资源搜索的能力](https://code.visualstudio.com/)

![[Pasted image 20240614125620.png]]
**推荐用Bing搜索因为有关编程他显示结果很准确**
**推荐FireFox因为他开源插件多**
![[Pasted image 20240614125819.png]]
点这个会出来更多选项，选择一个下载
### Windows
直接下载WindowsX64 Stable安装即可
### Linux
需要到文件路径，打开Terminal，然后输入"dpkg -i ",拖动文件到Terminal即可自动补全路径（XFCE4的文件管理器有这功能，其他的文件管理器应该也有）
如果出现error红色，一般是依赖问题，Terminal输入“apt --fix-broken install”或者“apt --fix-missing install”安装完后再运行一次dpkg那一步的命令即可


---


<b><div align='center' ><font size='5'>安装后配置</font></div></b>
<b><div align='center' ><font size='4'>Linux特殊部分</font></div></b>
**由于Vscode是用Electron框架，如果是在容器里一般需要指定nosanbox和userdata目录
在DesktopLauncher界面命令框（假如你是通过包管理器apt或者dpkg安装一般都有命令链接）
直接输入“code --no-sandbox --user-data-dir ~”，“~”可以自己替换为任意目录，只要你有权限**

<b><div align='center' ><font size='4'>通用部分</font></div></b>
<b><center>先点击</center></b>
 ![[Web编程/WebTechniqueForLearners/VSCODE配置/VSPic/Plugin.PNG]]
<b><center>进入插件搜索界面</center></b>
![[Chinese.PNG]]
<b>点击蓝色小按钮下载安装即可
VSC会提示你要不要重启换语言，点击接受或者Yes</b>


---

<b><div align='center' ><font size='5'>认识VSCode</font></div></b>

![[VS.PNG]]![[Exp.PNG]]
**选择某个选项就会出现蓝色边，并且会出现视图显示其详细界面
从上到下依次是**

<b><center>1.文件/文件夹管理</center>
<center>2.文件搜索</center>
<center>3.Git功能</center>
<center>4.Debug（这个只对于编译型语言有用，Web开发另有插件）</center>
<center>5.插件商店界面</center></b>


---

<b><div align='center' ><font size='5'>插件安装</font></div></b>
##### 必要插件
![[LivePreview.PNG]]
**可以在侧边栏实时更新，比手动开浏览器F5刷新方便**

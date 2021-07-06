## Graphic User Interfaces and EasyGui

Graphic User Interfaces 图形用户界面

For introduction to GUI, we can use [EasyGui](http://easygui.sourceforge.net)).

IDLE may cause problems to EasyGui, but using the following method it works well for me.

I follow [this](https://www.programmersought.com/article/9571128907/) to install and import EasyGui to my Mac: 
1. Because mac contains instructions that can execute pip, you can use the pip command to install easygui. 
So open the mac terminal and enter the command `pip3 install easygui`.

2. This return means success as:
Collecting easygui

  Downloading easygui-0.98.2-py2.py3-none-any.whl (92 kB)
  
   |████████████████████████████████| 92 kB 4.5 MB/s 
     
Installing collected packages: easygui

Successfully installed easygui-0.98.2

3. Run the easygui command in python3.7 IDLE,
```Python
#method 1 to import easygui
import eastgui easygui.msgbox('Hello Word!')
runs as follows
```
then a window with Hello Word! and a 'OK' button pops out. Click 'OK' to close it.

4. This way you can run the gui interaction directly in python, welcome everyone to guide.

There are alternative ways to import easygui, as below.
```Python
#method 2
from easygui import *
msgbox('Hello')

#method 3
import easygui as g
g.msgbox('Hello')
```
Also, we can directly open the .py file by Python, avoiding using IDLE

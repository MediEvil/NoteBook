## python 技巧

1. 设置虚拟环境
在项目目录下打开bash输入以下指令
```bash
python3 -m venv venv/
```
这样可以创建一个python的虚拟环境
```bash
source venv/bin/activate
```
这样可以激活虚拟环境
```bash
deactivate
```
这样退出

2. 逐行安装requirements
```bash
FOR /F %k in (requirements.txt) DO pip install %k
```
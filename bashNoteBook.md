## iTerm2 技巧

1. macOS单独设置app的程序语言

一般我比较习惯英文版的macOS，但是在英文版的情况下，微信自动也变成了英文版，没有办法使用转文字功能，所以需要设置微信的语言为中文。


首先查询app的包名

```bash
mdls -name kMDItemCFBundleIdentifier /Applications/WeChat.app
```

然后修改默认语言为中文

```bash
defaults write com.tencent.xinWeChat AppleLanguages '("zh_CN")'
```

可以用以下指令进行查询
```bash
defaults read com.tencent.xinWeChat AppleLanguages
```

下附语言代码
ar = Arabic
cs = Czech
da = Danish
de = German
el = Greek
en = English(US)
es = Spanish
fi = Finnish
fr = French
he = Hebrew
hu = Hungarian
id = Indonesian
it = Italian
ja = Japanese
ko = Korean
nl = Netherlands
no = Norwegian
pl = Polish
pt_PT = Portuguese
ru = Russian
sk = Slovak
sv = Swedish
th = Thai
tr = Turkish
zh_CN = Chinese Simplified
zh_TW = Chinese Taiwan

2. 刷新dock栏
```bash
killall Dock
```

3. 查找端口占用并杀进程
```bash
lsof -i:8080
```

4. 给当前用户分配文件夹权限
```bash
sudo chown -R $(whoami) /usr/local
```

5. 打开windows压缩的zip包
```bash
ditto -x -k zip_file_path unzip_destinatio_path
```
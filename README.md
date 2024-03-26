# run-pgm-on-mac
在开始之前要提醒您：完成后请不要关闭终端，不然会结束进程！！！


mac和Linux无异，无非就是搭建python环境的指令不同

首先安装一个homebrew，这个工具对于新手来说非常友好：

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

运行后请耐心等待几分钟，下载的文件可能有点多
在拉取项目之前，首先更新 git ，否则之后可能出现无法更新的情况。

```
brew install git
```

拉取项目至 downloads 目录。(当然这里可以更改)：

```
cd downloads && git clone https://github.com/TeamPGM/PagerMaid-Pyro.git pgp && cd pgp
```

若无法拉去请使用root模式：

```
sudo -i
```

随后用brew更新安装python3：

```
brew install python3 imagemagick webp neofetch zbar xml2 libxslt tesseract
```

安装软件包过程中，请等待一段时间，安装完成后，继续进行以下操作。

接下来教程可参考官方的文档，以下仅做搬运

首先启用虚拟环境：

```
python3 -m venv venv
source venv/bin/activate
```

可以看到命令行前面多了一个 (venv) ，即表示启用成功。

更新一下 pip：
```
python3 -m pip install --upgrade pip
```

接下来安装 Python 依赖包：
```
pip3 install -r requirements.txt
```

请确保以上命令输入时均处于虚拟环境中，即有 (venv) 标志。
若退出了虚拟环境，若还在虚拟环境中请忽略此步骤。
可以使用以下命令重新进入虚拟环境：

```
source venv/bin/activate
```

执行以下命令，将配置文件 config.gen.yml 复制一份并且命名为 config.yml：

```
cp config.gen.yml config.yml
```

修改 config.yml：

```
vim config.yml
```

若不会使用vim编辑器请去搜索学习，这里不做介绍

修改配置文件中的api_id和api_hash即可

日志及报错信息记录 (可选) ：
```
log: "False"    # False 代表禁用，True 代表启用
log_chatid: "503691334"    # 这里填写记录用的群组或频道ID
```
代理 (可选) ：
```
proxy_addr: ""    # socks5 代理地址
proxy_port: ""    # socks5 代理端口
http_addr: ""    # http 代理地址
http_port: ""    # http 代理端口
mtp_addr: ""    # mtp 代理地址
mtp_port: ""    # mtp 代理端口
mtp_secret: ""    # mtp 代理密钥
```

二维码登录 (可选) ：
```
qrcode_login: "False"    # False 代表禁用，True 代表启用
```
登录账号
请确保仍在虚拟环境中，即有 (venv) 标志，然后运行以下命令：

```
python3 -m pagermaid
```

此步需要填入完整的电话号码 (eg：+18888888888，需要带上国际区号) 然后 Telegram 会向你的其他客户端发送验证码，少数用户会向手机号发送验证码，填入验证码后，回车，如有两步验证密码，则再输入两步验证密码即可。

```
Enter phone number or bot token:    #此处填入手机号
Is "+18888888888" correct? (y/N):    # 号码显示正确输入 y ,错误输入 n
The confirmation code has been sent via Telegram app
Enter confirmation code:    # 此处输入 Telegram APP 中收到的验证码
# 如果设置了两步验证，则会出现以下提示
The two-step verification is enabled and a password is required
Password hint: None
Enter password (empty to recover):    # 此处输入两步验证密码
```
注：完成后请不要关闭终端，不然会结束进程！

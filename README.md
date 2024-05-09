# 功能
1. 运行-c/--command参数指定的任务（可用-f/--flag参数指定此次任务的标识）
2. 任务运行成功或失败后，由-s/--sender_mail参数指定的邮箱（需用-p/--password指定邮箱授权码）发送邮件
3. 发送失败或成功信息到-r/--receiver_mail参数指定的邮箱

# 注意
1. -c及-r参数为必须参数
2. 若不指定-f参数，则默认标识为当前时间
3. 若不指定-s和-p参数，则使用程序内部提供的邮箱

# 下载并增加配置以方便使用
```shell
# 1. 下载
git clone git@github.com:ZFF00/run.git
# 2. 将run文件放在~/bin目录下
mkdir ~/bin
cp ./run/run ~/bin
chmod +x ~/bin/run
# 3. 将~/bin目录添加到环境变量中
echo 'export PATH=$PATH:~/bin' >> ~/.bashrc
# 4. 自定义命令以更简洁地使用, 添加收件人邮箱地址, 假设为123456789@qq.com
echo 'alias run="run --receiver_mail 123456789@qq.com "' >> ~/.bashrc
# 5. 激活配置, 只需执行一次
source ~/.bashrc
# 6. 使用测试，运行ls命令, 当运行任务时间较长时推荐在后台运行
run -f 测试任务 -c ls
```

# 用法
```shell
usage: run [-h] [-f FLAG [FLAG ...]] -c COMMAND [COMMAND ...] [-s SENDER_MAIL] [-p PWD] -r RECEIVER_MAIL

运行指定的任务, 并将成功或失败信息发送到邮箱

options:
  -h, --help            show this help message and exit
  -f FLAG [FLAG ...], --flag FLAG [FLAG ...]
                        此次任务的标识
  -c COMMAND [COMMAND ...], --command COMMAND [COMMAND ...]
                        要运行的命令, 空格隔开, 若命令中有“-”，请用引号将整个命令括起来
  -s SENDER_MAIL, --sender_mail SENDER_MAIL
                        发信人邮箱
  -p PWD, --pwd PWD     发信人邮箱授权码
  -r RECEIVER_MAIL, --receiver_mail RECEIVER_MAIL
                        收信人邮箱
```
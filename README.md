# KORTHO
## 下载地址
| windows | linux |
|  :----  | :----  |
|  [kortho_miner_windows_0.1.0](https://www.kortho.org/file/windows/miner_windows_010.zip)  | [kortho_miner_linux_0.1.0](https://www.kortho.org/file/linux/miner_linux_010.zip) |
   
## 配置安装：
### windows下：
        第一步 若首次安装则在工作目录下创建挖矿目录，如 D:/miner（非C盘），更新升级则跳过。

        第二步 若首次安装则将下载的windows挖矿软件包拷贝到D:/miner下并解压，若是升级更新则在其他地方解压只替换升级的执行程序。

        第三步 若首次安装则进入生成的解压目录，修改config下"korthoConf.yaml"的配置文件，更新升级则跳过：
            （1）：找到'miningaddr'参数修改为自己的矿工地址，如 miningaddr : "Kto***"，
                  种子节点: greamhost: "种子节点ip"，
                  p2pconfig配置（有公网Ip情况下配置以下两个，无公网IP则默认）:
                       advertiseaddr : "本机公网IP"，
                       jionmembers: "种子节点ip".
                       保证相应端口（10001,10002，13869）开放。
                  ***注（非常关键的一步）：首次安装必须修改配置文件，之后升级更新则不需要修改配置，若替换了配置文件则需要重新按照以上配置,
                        种子节点附带在安装包中。

        第四步 点开windows开始菜单，在搜索框中输入“cmd”，在搜索结果中，对着命令提示符程序，单击鼠标右键，菜单中点击选择“以管理员身份运行”,如图: 
![Image text](.\picture\cmd1.jpg)               
            （0）：键入命令:

```             先执行下一行命令跳转到miner目录：
                [C:\Users\Administrator>] cd /d E:\miner\miner_windows
                然后再根据有无公网ip执行下面对应的其中一个命令！！！
                [有公网ip节点]->: .\miner.exe -n 100 -s 1   注：（保证相应端口（10001,10002，13869）开放）
                [无公网ip节点]->: .\miner.exe -n 100 -s 1 -m 1
             
```
            （1）：-n 表示 开启 cpu 数量
            （2）：-s 表示 是否恢复数据（固定为1）
            （3）：-m 表示 若无公网IP（固定为1），若有公网IP无本参数

        第五步 回车执行命令，开启挖矿。

        第六步 查询挖矿：打开自己的矿工钱包->数据->当前矿工数据。

### linux下：
        脚本安装：首次安装则在工作目录下创建挖矿目录，如 /work/miner，然后将installminer.sh拷贝到miner目录执行 bash installminer.sh 根据提示安装即可。
        
        手动安装：
        第一步 若首次安装则在工作目录下创建挖矿目录，如 /work/miner，更新升级则跳过。

        第二步 若首次安装则将下载的 linux 挖矿软件包拷贝到/work/miner下并解压，若是升级更新则在其他地方解压只替换升级的执行程序。

        第三步 若首次安装则进入生成的解压目录，修改config下"korthoConf.yaml"的配置文件，更新升级则跳过：
            （1）：找到'miningaddr'参数修改为自己的矿工地址，如 miningaddr : "Kto***"，
                  种子节点: greamhost: "种子节点ip"，
                  p2pconfig配置（有公网Ip情况下配置以下两个，无公网IP则默认）:
                      advertiseaddr : "本机公网IP"，
                      jionmembers: "种子节点ip".
                  ***注（非常关键的一步）：首次安装必须修改配置文件，之后升级更新则不需要修改配置，若替换了配置文件则需要重新按照以上配置，
                        种子节点附带在安装包中。
            （2）：执行下面两个命令:
```
               [若首次运行]-> chmod +x miner 

               [有公网ip节点]->: sudo ./miner -n=100 -s=1     注：（保证相应端口（10001,10002，13869）开放）           
               [无公网ip节点]->: sudo ./miner -n=100 -s=1 -m=1
             
```             
            （3）：-n 表示 开启 cpu 数量
            （4）：-s 表示 是否恢复数据（固定为1）
            （5）：-m 表示 若无公网IP（固定为1），若有公网IP无本参数


        第四步 回车执行命令，开启挖矿。

        第五步 查询挖矿：打开自己的矿工钱包->数据->当前矿工数据。

## 源码安装：
        不管linux或是windows环境，首先要保证安装了go环境。

### windows下：
            第一步 编译源码：            
                （0）：若首次安装则在工作目录下创建挖矿目录，如 D:/miner，然后在miner下创建config目录，更新升级则跳过。
                （1）：进入源码目录更新源码，打开windows命令行执行：go env -w GOOS=windows|go build -o .\miner.exe .\main.go。

            第二步 进入miner目录，将生成的miner.exe 拷贝当前目录下，若首次安装则将源码pkg/config/korthoConf.yaml拷贝到当前/config目录下。

            第三步 若首次安装则必须修改/miner/config下"korthoConf.yaml"的配置文件，更新升级则跳过：            
                （1）：找到'miningaddr'参数修改为自己的矿工地址，如 miningaddr : "Kto***"，
                       种子节点: greamhost: "种子节点ip"，
                        P2P配置（有公网Ip情况下配置，无公网IP则默认）:
                            advertiseaddr : "本机公网IP"，
                            jionmembers: "种子节点ip".
                       ***注（非常关键的一步）：首次安装需要按以上修改配置文件，之后升级更新则不需要修改配置。
            第四步 点开windows开始菜单，在搜索框中输入“cmd”，在搜索结果中，对着命令提示符程序，单击鼠标右键，菜单中点击选择“以管理员身份运行”,如图: 
![Image](.\picture\cmd1.jpg)
                （0）：然后键入命令: 
```
                    先执行下一行命令跳转到miner目录：
                    [C:\Users\Administrator>] cd /d E:\miner\miner_windows
                    然后再根据有无公网ip执行下面对应的其中一个命令！！！
                    [有公网ip节点]->: .\miner.exe -n 100 -s 1   注：（保证相应端口（10001,10002，13869）开放）
                    [无公网ip节点]->: .\miner.exe -n 100 -s 1 -m 1

```
                （1）：-n 表示 开启 cpu 数量
                （2）：-s 表示 是否恢复数据（固定为1）
                （3）：-m 表示 若无公网IP（固定为1），若有公网IP无本参数 

            第五步 回车执行命令，开启挖矿。

            第六步 查询挖矿：打开自己的矿工钱包->数据->当前矿工数据。

### linux下：
            第一步 编译源码：
                （0）：若首次安装则在工作目录下创建挖矿目录，如 /work/miner，然后在miner下创建config目录，更新升级则跳过。
                （1）：进入源码目录更新源码，再命令行执行：go build -o /work/miner .\main.go。

            第二步 若首次安装则进入miner目录，将源码pkg/config/korthoConf.yaml拷贝到/work/miner/config目录下，更新升级则跳过。

            第三步 若首次安装则进入/work/miner/config，必须修改"korthoConf.yaml"的配置文件，更新升级则跳：
                （1）：找到'miningaddr'参数修改为自己的矿工地址，如 miningaddr : "Kto***"，
                       种子节点： greamhost: "种子节点ip"，
                       P2P配置（有公网Ip情况下配置，无公网IP则默认）:
                            advertiseaddr : "本机公网IP"，
                            jionmembers: "种子节点ip".
                       ***注（非常关键的一步）：首次安装需要按以上修改配置文件，之后升级更新则不需要修改配置。
            第四步 /work/miner/：
                （0）：每次删除kortho.db,然后键入命令: 
```
                   [有公网ip节点]->: sudo ./miner -n=100 -s=1    注：（保证相应端口（10001,10002，13869）开放）            
                   [无公网ip节点]->: sudo ./miner -n=100 -s=1 -m=1

```
                （1）：-n 表示 开启 cpu 数量
                （2）：-s 表示 是否恢复数据（固定为1）
                （3）：-m 表示 若无公网IP（固定为1），若有公网IP无本参数  

            第五步 回车执行命令，开启挖矿。

            第六步 查询挖矿：打开自己的矿工钱包->数据->当前矿工数据。

## [领取测试币](http://faucet.kto.dappbox.finance/#/index)
   地址：http://faucet.kto.dappbox.finance/#/index ,
   下拉框选取mKTO选项，然后填入领币地址， 然后点击确认。


# aliyunDeploy  
## 阿里云配置部署
#### 一、部署 Node.js项目 （CentOS 7.2 , Node 10.15.2-x64）<br>

###### 1. 使用二进制文件安装
>该部署过程使用的安装包是已编译好的二进制文件，解压之后，在bin文件夹中就已存在node和npm，无需手工编译
>>安装步骤：
```
    i:  wget命令下载Node.js安装包。该安装包是编译好的文件，解压之后，在bin文件夹中就已存在node和npm，无需重复编译。
    wget https://nodejs.org/dist/v10.15.2/node-v10.15.2-linux-x64.tar.xz
```
```
    ii:  解压文件。
        tar xvf node-v10.15.2-linux-x64.tar.xz
```
```
    iii:  创建软链接，使node和npm命令全局有效。通过创建软链接的方法，使得在任意目录下都可以直接使用node和npm命令：
        ln -s /root/node-v10.15.2-linux-x64/bin/node /usr/local/bin/node
        ln -s /root/node-v10.15.2-linux-x64/bin/npm /usr/local/bin/npm
```
```
    iv:  查看node、npm版本
        node -v
        npm -v
```
```
    v:  至此，Node.js环境已安装完毕。软件默认安装在/root/node-v6.9.5-linux-x64/目录下。如果需要将该软件安装到其他目录（如：/opt/node/）下，请进行如下操作:
        mkdir -p /opt/node/
        mv /root/node-v10.15.2-linux-x64/* /opt/node/
        rm -f /usr/local/bin/node
        rm -f /usr/local/bin/npm
        ln -s /opt/node/bin/node /usr/local/bin/node
        ln -s /opt/node/bin/npm /usr/local/bin/npm
```
```
    注：
        运行项目： node ~/example.js 
        您也可以使用命令将项目置于后台运行： node ~/example.js & 
        使用命令查看项目端口是否存在： netstat -tpln
```



#### 二、安装Git （CentOS 7.2 , Git1.8.3.1-x64）<br>
###### 1. 安装步骤：
```
    i:  yun 命令进行安装
    yum install git 
```
```
    ii:  查看git 版本
    git --version 
```
```
    iii:  对git进行初始化设置
    git config --global user.name "tomatocc" (tomatocc是git的用户名) 然后回车即可
	git config --global user.email "tomatocc@sina.com" (tomatocc@sina.com是git的用户名邮箱) 然后回车即可

```
```
    iv:  生成授权证书
    Git的授权证书是基于公钥和私钥的证书体系，所以需要证书体系 生成证书:（1：表示文件名，2：表示生成证书的密码，3：表示确认密码），然后回车即可
    ssh-keygen -t rsa -C "tomatocc@sina.com
```
```
    v:  切换到ssh目录下 查看证书是否生成
    cd ~/.ssh/ 
```
```
    vi:  cat id_rsa.pub 查看公钥内容，并复制公钥内容
```
```
    vii:  进入GitHub网站的 Settings 页面的 【SSH and GPG Keys】-----> 【New SSH Key】 栏添加,将该公钥黏贴到github中的key里面，然后点击【Add SSH Key】
```
```
    viii:  验证git的配置是否正确，是否能链接github
    ssh git@github.com
```
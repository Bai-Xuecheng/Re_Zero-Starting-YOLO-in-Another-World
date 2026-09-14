# pip 使用国内镜像源

> pip 默认使用 PyPI 官方源，国内访问有时较慢。可以通过 `-i` 临时指定国内镜像源，或通过 `pip config` 设置默认镜像源，提高 Python 包下载速度。

默认情况下 pip 使用的是国外的镜像，在下载的时候速度非常慢，本节我们介绍使用国内清华大学的源，地址为：

```bash
https://pypi.tuna.tsinghua.edu.cn/simple
```

我们可以直接在 pip 命令中使用 ```-i``` 参数来指定镜像地址，例如：

```bash
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple some-package
```

以上命令使用清华源安装，```some-package``` 为所需要安装的包。

## 设为默认

升级 pip 到最新的版本后进行配置：

```bash
python -m pip install --upgrade pip
pip config set global.index-url https://mirrors.tuna.tsinghua.edu.cn/pypi/web/simple
```

如果 pip 默认源的网络连接较差，临时使用清华的镜像站来升级 pip：

```bash
python -m pip install -i https://mirrors.tuna.tsinghua.edu.cn/pypi/web/simple --upgrade pip
```

## 修改配置

如果需要全局修改，则需要修改配置文件。

- **Linux/Mac OS 环境**

    配置文件位置在 ```~/.pip/pip.conf``` （如果不存在创建该目录和文件）：

    ```
    mkdir ~/.pip
    ```

    打开配置文件 ```~/.pip/pip.conf```，修改如下：

    ```
    [global]
    index-url = https://pypi.tuna.tsinghua.edu.cn/simple
    [install]
    trusted-host = https://pypi.tuna.tsinghua.edu.cn
    ```

    查看镜像地址：

    ```
    $ pip config list
    global.index-url='https://pypi.tuna.tsinghua.edu.cn/simple'
    install.trusted-host='https://pypi.tuna.tsinghua.edu.cn'
    ```

- **Windows 环境**
    需要在当前对用户目录下（```C:\Users\xx\pip```，xx 表示当前使用对用户，比如张三）创建一个 ```pip.ini``` 在 ```pip.ini``` 文件中输入以下内容:

    ```
    [global]
    index-url = https://pypi.tuna.tsinghua.edu.cn/simple
    [install]
    trusted-host = pypi.tuna.tsinghua.edu.cn
    ```
    
## 其他国内镜像源(👀 镜像源更换位置在 ```-i``` 之后)

- **清华大学TUNA镜像源：** https://pypi.tuna.tsinghua.edu.cn/simple
- **阿里云镜像源：** http://mirrors.aliyun.com/pypi/simple/
- **中国科学技术大学镜像源：** https://mirrors.ustc.edu.cn/pypi/simple/
- **华为云镜像源：** https://repo.huaweicloud.com/repository/pypi/simple/
- **腾讯云镜像源：** https://mirrors.cloud.tencent.com/pypi/simple/


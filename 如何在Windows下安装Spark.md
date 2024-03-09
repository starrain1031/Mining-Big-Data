首先，最新的Spark版本是3.5.1，Spark需要java环境的支持，jdk的安装是必须的。3.5.1版本的Spark支持Java 8/11/17，以及3.8以上版本的Python。

不推荐8u371版本前的Java 8。
对于 Java 11，`-Dio.netty.tryReflectionSetAccessible=true`需要对 Apache Arrow 库进行设置。这可以防止`java.lang.UnsupportedOperationException: sun.misc.Unsafe or java.nio.DirectByteBuffer.(long, int) not available`Apache Arrow 在内部使用 Netty 时出现错误。
因此推荐从官方站下载并安装Java 17。

### 1. 在Anaconda中安装额外的Python环境，3.8版本以上即可
### 2. 在Anaconda安装的python环境下，终端输入命令`conda install –c conda-forge pyspark`完成安装
### 3. 配置环境变量，务必注意，一定要让java被全局使用，因为pyspark必须调用java环境。

添加环境变量 `JAVA_HOME`, 值为jdk安装根目录
添加环境变量 `SPARK_HOME`, 值为pyspark根目录
终端输入命令 `python -c "import pyspark; print(pyspark.__file__)"`
此命令用于寻找pyspark的安装目录
因为调用pyspark也会使用python环境来进行dataframe的操作,
添加环境变量 `PYSPARK_PYTHON`，值为小写的`python`
##### 务必注意，如果用conda安装pyspark，pyspark的根目录在C:\\用户名\\anaconda\\envs\\环境名\\Lib\\site-packages\\pyspark

##### 只有直接在命令行安装的python环境，以及pyspark，才会根目录才在...\\Python\\scripts

两个环境变量添加完后，需要将他们加入Path中，以在找到目录后进一步找到可执行文件，因此在path中新建值
`%JAVA_HOME%\\bin`
`%SPARK_HOME%\\bin`

input函数不弹出输入框是vscode中 jupyter notebook 插件的兼容问题
解决办法1：使用python 3.8 版本，同时在conda环境中安装nb-conda。
安装后可以在jupyter notebook 中选择conda环境作为 Kernel。
解决办法2：使用pycharm作为编辑器
解决办法3：直接赋值，去掉该函数
解决办法4：用Google Colab运行jupyter notebook
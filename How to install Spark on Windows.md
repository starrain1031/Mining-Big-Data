First of all, the latest Spark version is 3.5.1, Spark needs the support of the java environment, and the installation of jdk is required. Spark version 3.5.1 supports Java 8/11/17 and Python version 3.8 or later.

Java 8 prior to version 8u371 is not recommended.
For Java 11, `-Dio.netty.tryReflectionSetAccessible=true` requires the Apache Arrow library to be set. This prevents `java.lang.UnsupportedOperationException: sun.misc.Unsafe or java.nio.DirectByteBuffer. (long, int) not available`Apache Arrow has an error when using Netty internally.
Therefore, it is recommended to download and install Java 17 from the official website.

### 1. Install an additional Python environment in Anaconda, version 3.8 or later
### 2. In the Python environment where you installed it with Anaconda, run the `conda install –c conda-forge pyspark` command to complete the installation
### 3. When configuring environment variables, it is important to note that Java is used globally, as PySpark must call the Java environment.

Add the environment variable `JAVA_HOME`, the value of which is the root directory of the JDK installation
Add the environment variable `SPARK_HOME` with the value of pyspark root
Terminal input command `python -c "import pyspark; print(pyspark.__file__)"`
This command is used to find the directory where pyspark is installed
Because calling pyspark will also use the python environment to operate dataframes,
Add environment variable `PYSPARK_PYTHON` with lowercase `python` as its value.
##### It is important to note that if pyspark is installed with conda, the root of pyspark is in C:\\username\\anaconda\\envs\\environment_\Lib\\site-packages\\pyspark

##### Only python environments installed directly on the command line, as well as pyspark, will be rooted in ...\\Python\\scripts

After the two environment variables are added, they need to be added to the path to find the executable further after finding the directory, so create a new value in the path
`%JAVA_HOME%\\bin`
`%SPARK_HOME%\\bin`

The input function does not pop up the input box, which is a compatibility issue with the Jupyter notebook plug-in in vscode
Solution 1: Use python 3.8 and install nb-conda in the conda environment.
After installation, you can select the conda environment as the kernel in the jupyter notebook.
Solution 2: Use pycharm as the editor
Solution 3: Assign a value and remove the function
Solution 4: Use Google Colab to run jupyter notebook
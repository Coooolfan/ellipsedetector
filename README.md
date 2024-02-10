ellipsedetector
===============

The project offers an implementation of the *Randomized Hough Transform for Ellipse Detection*, as described in Basca et al.: Cosmin A. Basca, Mihai Talos and Remus Brad, Randomized Hough Transform for Ellipse Detection with Result Clustering, Proceedings of IEEE EUROCON 2005, The International Conference on "Computer as a Tool", vol. II, pp.1397-1400, Belgrade Serbia November 2005, ISBN 1-4244-0049-X, http://remus.ulbsibiu.ro/publications/papers/eurocon2005.pdf

---

该项目提供了*椭圆检测的随机霍夫变换*的实现，如Basca等人在《IEEE EUROCON 2005》会议上的论文中所述：Cosmin A. Basca, Mihai Talos和Remus Brad, "Randomized Hough Transform for Ellipse Detection with Result Clustering"，收录于《Computer as a Tool》国际会议论文集，第II卷，第1397-1400页，2005年11月，塞尔维亚贝尔格莱德，ISBN 1-4244-0049-X，可参考链接：http://remus.ulbsibiu.ro/publications/papers/eurocon2005.pdf

---

相比原始项目，该项目使用Maven描述了所需的JAR文件。您可以直接将该项目导入您的IDE并运行。

请注意，如果IntelliJ IDEA无法自动识别资源根目录，您需要在IDEA左侧的项目文件列表中右键单击"src"文件夹，选择"将目录标记为" -> "资源根目录"。

---
**不论以和种参数运行，您都需要指定jvm虚拟机参数`-Dcom.sun.media.jai.disableMediaLib=true`**

**您需要在java1.8环境下运行，以避免出现由于由于模块化系统限制导致的报错**

- GUI界面
    ```shell
    java -Dcom.sun.media.jai.disableMediaLib=true -jar ellipsedetector-0.0.2-jar-with-dependencies.jar
    ```

- 命令行
    ```shell
    java -Dcom.sun.media.jai.disableMediaLib=true -jar ellipsedetector-0.0.2-jar-with-dependencies.jar <image> <minA> <maxA> <minB> <maxB> <quality/minVotes> <threshold/idleStop> <maxPairs> <debug>
    ```
  
    - image：String image 输入图像的路径。 
    - minA: Integer minMajorAxis：椭圆的最小长轴长度，用于限制检测到的椭圆的大小。
    - maxA: Integer maxMajorAxis：椭圆的最大长轴长度，用于限制检测到的椭圆的大小。
    - minB: Integer minMinorAxis：椭圆的最小短轴长度，用于限制检测到的椭圆的大小。
    - maxB: Integer maxMinorAxis：椭圆的最大短轴长度，用于限制检测到的椭圆的大小。
    - quality/minVotes: Integer minVotes：检测到的椭圆需要的最小投票数。在霍夫变换中，每个可能的椭圆都会得到一些投票，只有当投票数超过这个值时，程序才认为检测到了一个椭圆。
    - threshold/idleStop: Integer idleStop：阈值，当连续多次迭代没有检测到新的椭圆时，算法会停止。
    - maxPairs: Float maxPairs：一个比例值，表示最大的点对数量，这些点对用于生成可能的椭圆。这个值是图像中边缘点数量的百分比。
    - debug: Boolean debug：请设置为1，否则程序不会有输出。

    eg.

    ```shell
    $ java -jar ellipsedetector.jar -h
    Usage :
    java -jar RHED.jar
    java -jar RHED.jar <image> <minA> <maxA> <minB> <maxB> <quality/minVotes> <threshold/idleStop> <maxPairs> <debug>
    GUI will start if no arguments are given, GUI version parameters are defined [34,88,39,81,100,5000,0.5,1]
    ```
    ```shell
    java -Dcom.sun.media.jai.disableMediaLib=true -jar ellipsedetector-0.0.2-jar-with-dependencies.jar "C:/Users/YourUsername/Desktop/IndustryDataset/e5.png" 34 88 39 81 100 5000 0.5 1
    ```
**请注意，在Windows下，您可能会遇到如`错误: 找不到或无法加载主类 com.sun.media.jai.disableMediaLib=true`错误，请尝试使用双引号包裹虚拟机选项，即**
```shell
java "-Dcom.sun.media.jai.disableMediaLib=true" -jar ellipsedetector-0.0.2-jar-with-dependencies.jar
```
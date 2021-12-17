@[TOC]

<br>
<br>
<br>
<br>

# 一、创建 Android Studio 工程

---


<br>

在 Android Studio 欢迎界面 , 选择 " Create New Project " 创建新的 Android 应用 ; 
![在这里插入图片描述](https://img-blog.csdnimg.cn/233ac1520d5b4467bd7c3934205f3173.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6Z-p5puZ5Lqu,size_20,color_FFFFFF,t_70,g_se,x_16)

默认创建 Module 即可 , 应用的 Module 不能作为 Groovy 开发的工程 , 这里随意即可 , Groovy 开发工程需要额外创建 Java 依赖库 Module , 然后基于 Java 依赖库 Module 进行改造 ; 

![在这里插入图片描述](https://img-blog.csdnimg.cn/73e7c35257df45138fd67faca01e7922.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6Z-p5puZ5Lqu,size_20,color_FFFFFF,t_70,g_se,x_16)

设置工程名称 , 然后点击 " Finish " 完成设置 ; 
![在这里插入图片描述](https://img-blog.csdnimg.cn/ca7d1211049a4a358221734037f24439.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6Z-p5puZ5Lqu,size_20,color_FFFFFF,t_70,g_se,x_16)

新创建的 Android 工程是一个空白工程 ; 

![在这里插入图片描述](https://img-blog.csdnimg.cn/bdd7307af3b64635b6b547175cec1c27.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6Z-p5puZ5Lqu,size_20,color_FFFFFF,t_70,g_se,x_16)








<br>
<br>
<br>
<br>

# 二、创建 Java or Kotlin Library 类型的 Module 

---


<br>

选择 " 菜单栏 / File / New / New Module ... " 选项 , 在本工程下创建 Module 工程 ; 

![在这里插入图片描述](https://img-blog.csdnimg.cn/0856768824f14c4580ad90a729aea163.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6Z-p5puZ5Lqu,size_20,color_FFFFFF,t_70,g_se,x_16)


选择创建 " Java or Kotlin Library " 的 Module ; 

![在这里插入图片描述](https://img-blog.csdnimg.cn/07081b98eee6483b86225e11ff178487.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6Z-p5puZ5Lqu,size_20,color_FFFFFF,t_70,g_se,x_16)


创建完后的依赖库 Module ; 

![在这里插入图片描述](https://img-blog.csdnimg.cn/6a1fd5e571c8423191ab0eb53a512b68.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6Z-p5puZ5Lqu,size_20,color_FFFFFF,t_70,g_se,x_16)









<br>
<br>
<br>
<br>

# 三、改造 Java or Kotlin Library 类型的 Module

---


<br>


**原来的 build.gradle 配置 :** 

```java
plugins {
    id 'java-library'
}

java {
    sourceCompatibility = JavaVersion.VERSION_1_7
    targetCompatibility = JavaVersion.VERSION_1_7
}
```

<br>

**配置 Groovy 插件 :** 在 plugins 中 , 配置 

```java
id 'groovy'
```

应用 Groovy 插件 ; 

<br>

**添加依赖 :** 

```java
dependencies {
    implementation localGroovy()
}
```

<br>


**配置完成的支持 Groovy 的 build.gradle :** 

```java
plugins {
    id 'java-library'
    id 'groovy'
}

java {
    sourceCompatibility = JavaVersion.VERSION_1_7
    targetCompatibility = JavaVersion.VERSION_1_7
}

dependencies {
    implementation localGroovy()
}
```

配置完毕后 , 编译该 Module 项目 , 编译成功 ; 

![在这里插入图片描述](https://img-blog.csdnimg.cn/5eb17177863644c684c36876966937c3.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6Z-p5puZ5Lqu,size_20,color_FFFFFF,t_70,g_se,x_16)



<br>
<br>
<br>
<br>

# 四、编写 Groovy 代码文件并运行

---


<br>

右键点击该 Module 的 main 目录 , 选择 " New / Directory " 选项 , 


![在这里插入图片描述](https://img-blog.csdnimg.cn/a0c4e4412c8c4ad492b851134b762481.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6Z-p5puZ5Lqu,size_20,color_FFFFFF,t_70,g_se,x_16)

可以看到可以创建 groovy 目录 ; 

![在这里插入图片描述](https://img-blog.csdnimg.cn/e20e5a85e9b645bca01a7bd35f962de4.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6Z-p5puZ5Lqu,size_20,color_FFFFFF,t_70,g_se,x_16)

右键点击 Groovy\groovy\src\main\groovy 目录 , 在弹出的菜单中选择 " New / File " 选项 , 



![在这里插入图片描述](https://img-blog.csdnimg.cn/7425da5b58654ac8865a20a3ccc1bf27.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6Z-p5puZ5Lqu,size_20,color_FFFFFF,t_70,g_se,x_16)

创建 Test.groovy 代码文件 ; 

![在这里插入图片描述](https://img-blog.csdnimg.cn/e95ebdd4b70e463ea2d7f15d4038f095.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6Z-p5puZ5Lqu,size_18,color_FFFFFF,t_70,g_se,x_16)

**编辑 Test.groovy 代码 :** 

```groovy
class Test {
    // Groovy 中的 main 函数
    def static main(def args) {
        // 在 Groovy 中可以使用 Java 语法
        System.out.println("Hello Groovy !!!")
    }
}
```

点击 main 函数左侧的运行按钮 , 运行该程序 , 运行结果如下 : 


![在这里插入图片描述](https://img-blog.csdnimg.cn/b361e6a513164de3a43b44ce0ea6f733.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA6Z-p5puZ5Lqu,size_20,color_FFFFFF,t_70,g_se,x_16)


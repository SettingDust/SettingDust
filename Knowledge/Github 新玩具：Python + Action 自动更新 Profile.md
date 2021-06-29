> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/349262045)

> 最近在Github上看到一些有意思的主页，就是用Github Action结合Profile来实现一些自动更新之类的操作。就自己用Python实现自动更新github activities和知乎的文章到自己的github首页上，也实现了全配置化，方便其…

> 最近在 Github 上看到一些有意思的主页，就是用 Github Action 结合 Profile 来实现一些自动更新之类的操作。就自己用 Python 实现自动更新 github activities 和知乎的文章到自己的 github 首页上，也实现了全配置化，方便其它人使用。  
> [Python + Github Action 实现自动更新 ProfIle](https://link.zhihu.com/?target=https%3A//github.com/dejavudwh) 欢迎 Star

先看一下一些大佬的骚操作

这两个都差不多，是通过 wakatime 和一些徽章、图片搭配起来

![](https://pic3.zhimg.com/v2-13728018bfebff8ead4f3d8eb3512c56_r.jpg)![](https://pic4.zhimg.com/v2-33307299945957ff989058e6e7a06e9b_r.jpg)

这个应该是我见过里面最骚气的了，直接在 readme 里实现了一个下棋，通过 issue 来互动。

![](https://pic3.zhimg.com/v2-70121ee717c4967df5afa3598b4e2796_b.gif)

下面这个就是我的了，通过 Python 和 Github Action 实现的知乎文章和 Github Activities 的自动更新。

![](https://pic2.zhimg.com/v2-98785a08b751fda9eb51785ffa2d5e01_b.gif)

实现
--

其实这个通过 Python 实现非常简单，一开始是用 Github 提供的 API 来抓取数据实现的自动更新，后面发现一个更好的方法：就是直接用 RSS。github 官方有提供 RSS，知乎可以找第三方做的 RSS。

之后就顺便做了配置驱动的，这样也方便别人使用，只要配置一下 RSS 源和参数就可以使用了

预备知识
----

*   把 markdown 放在首页就只要创建和用户同名的仓库，然后放至 readme 就可以了
*   [Github Action](https://link.zhihu.com/?target=https%3A//docs.github.com/en/actions)，但是其实只要看五分钟就够用做这个功能了

自动化获取信息
-------

之前用 Github 官方提供的 api 实现了更新最新的 Commit 信息，后面为了实现通过全配置的 RSS 源来自动更新，就暂时放弃这部分了，后面可能会再去实现全配置其它的 API。所以现在的实现就只有两部分了：

*   解析 RSS
*   生成指定格式
*   写入 README

![](https://pic3.zhimg.com/v2-66d43569238d8a6416e653ae9800693a_r.jpg)

使用
--

现在暂时总的代码也就 100 多行，但是其实 clone 之后自己配置一下就可以直接使用了

只需要配置两个地方，但是其实默认已经有知乎和 Github 了，如果不想用其它的源只要配置一个地方就好了

*   user

*   params：url 里需要用的参数都存储在这

*   feedList：也就是先声明一下自己的 feed  
    

*   disable：禁用
*   entryCount：显示个数

*   feeds：feed 的详细信息  
    

*   tagStartName：这个是放在 readme 里的标签名，也就是指定插入的地方
*   比如`<!-- GITHUB:START -->`

详细的配置见 github：[https://github.com/dejavudwh/dejavudwh/blob/main/usage.md](https://link.zhihu.com/?target=https%3A//github.com/dejavudwh/dejavudwh/blob/main/usage.md)

![](https://pic2.zhimg.com/v2-dc0d178e2ae9cb6df4218ddf3b04940d_r.jpg)![](https://pic1.zhimg.com/v2-933e82b56ef57256c1068b6571d7afc8_r.jpg)![](https://pic1.zhimg.com/v2-640ad80febfde4a1dfc03b7f8ae68ed0_r.jpg)
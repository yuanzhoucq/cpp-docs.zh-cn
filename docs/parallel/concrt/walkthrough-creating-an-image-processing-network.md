---
title: "演练：创建图像处理网络 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "创建图像处理网络 [并发运行时]"
  - "图像处理网络, 创建 [并发运行时]"
ms.assetid: 78ccadc9-5ce2-46cc-bd62-ce0f99d356b8
caps.latest.revision: 15
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：创建图像处理网络
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文档演示如何创建执行图像处理的异步消息块网络。  
  
 此网络根据图像的特性确定对其执行何种操作。  本示例使用数据流模型在网络上路由图像。  在数据流模型中，程序的各个独立组件通过发送消息来互相通信。  当某个组件收到消息时，它可以执行某项操作然后将该操作的结果传递给另一个组件。  相比之下，在控制流模型中，应用程序使用控制结构（例如条件语句和循环等等）控制程序中操作的顺序。  
  
 基于数据流的网络创建任务的管道。  管道的每个阶段并发执行整个任务的一部分。  与此类似的是汽车制造的装配线。  每辆汽车通过装配线时，一站组装车架，另一站则安装引擎，以此类推。  通过同时装配多辆汽车，装配线比一次装配整辆车拥有更高的产出。  
  
## 系统必备  
 在开始本演练之前，请阅读下列文档：  
  
-   [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [如何：使用消息块筛选器](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
  
-   [演练：创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)  
  
 建议您在开始本演练之前先了解 [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] 的基础知识。  有关 [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] 的更多信息，请参见 [GDI\+](_gdiplus_GDI_start_cpp)。  
  
##  <a name="top"></a> 各节内容  
 本演练包含以下各节：  
  
-   [定义图像处理功能](#functionality)  
  
-   [创建图像处理网络](#network)  
  
-   [完整示例](#complete)  
  
##  <a name="functionality"></a> 定义图像处理功能  
 本节介绍图像处理网络用于处理从磁盘读取的图像的支持函数。  
  
 `GetRGB` 和 `MakeColor` 函数分别提取和组合指定颜色的单个组件。  
  
 [!code-cpp[concrt-image-processing-filter#2](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-image-processing-network_1.cpp)]  
  
 `ProcessImage` 函数调用指定的 [std::function](../../standard-library/function-class.md) 对象，以转换 [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] [位图](https://msdn.microsoft.com/en-us/library/ms534420.aspx)对象中每个像素的颜色值。  `ProcessImage` 函数使用 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 算法并行处理位图的每一行。  
  
 [!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-image-processing-network_2.cpp)]  
  
 `Grayscale`、`Sepiatone`、`ColorMask` 和 `Darken` 函数调用 `ProcessImage` 函数，转换 `Bitmap` 对象中每个像素的颜色值。  所有这些函数都使用 lambda 表达式，来定义一个像素的颜色转换。  
  
 [!code-cpp[concrt-image-processing-filter#4](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-image-processing-network_3.cpp)]  
  
 `GetColorDominance` 函数也调用 `ProcessImage` 函数。  但是，该函数使用 [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) 对象计算是红色、绿色还是蓝色组件是图像的主色，而不是更改每个颜色的值。  
  
 [!code-cpp[concrt-image-processing-filter#5](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-image-processing-network_4.cpp)]  
  
 `GetEncoderClsid` 函数检索编码器的指定 MIME 类型的类标识符。  应用程序使用该函数检索位图的编码器。  
  
 [!code-cpp[concrt-image-processing-filter#6](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-image-processing-network_5.cpp)]  
  
 \[[Top](#top)\]  
  
##  <a name="network"></a> 创建图像处理网络  
 本节介绍如何创建对指定目录中每个 [!INCLUDE[TLA#tla_jpeg](../Token/TLA%23tla_jpeg_md.md)] \(.jpg\) 图像执行图像处理的异步消息块网络。  此网络会执行以下图像处理操作：  
  
1.  将 Tom 创作的所有图像都转换为灰阶。  
  
2.  对于以红色为主色的任何图像，删除绿色和蓝色组件，然后调暗图像。  
  
3.  对其他所有图像应用棕褐色调。  
  
 此网络仅应用符合其中一个条件的第一个图像处理操作。  例如，如果图像由 Tom 创作而且以红色为主色，则只会将该图像转换为灰阶。  
  
 网络执行每个图像处理操作后，它会将图像作为位图 \(.bmp\) 文件保存到磁盘。  
  
 以下步骤演示如何创建实现该图像处理网络，并将该网络应用到指定目录中所有 [!INCLUDE[TLA#tla_jpeg](../Token/TLA%23tla_jpeg_md.md)] 图像的函数。  
  
#### 创建图像处理网络  
  
1.  创建接受磁盘上目录名称的函数 `ProcessImages`。  
  
     [!code-cpp[concrt-image-processing-filter#7](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-image-processing-network_6.cpp)]  
  
2.  在 `ProcessImages` 函数中，创建 `countdown_event` 变量。  本演示稍后将会演示 `countdown_event` 类。  
  
     [!code-cpp[concrt-image-processing-filter#8](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-image-processing-network_7.cpp)]  
  
3.  创建将 `Bitmap` 对象与其原始文件名关联的 [std::map](../../standard-library/map-class.md) 对象。  
  
     [!code-cpp[concrt-image-processing-filter#9](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-image-processing-network_8.cpp)]  
  
4.  添加以下代码以定义图像处理网络的成员。  
  
     [!code-cpp[concrt-image-processing-filter#10](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-image-processing-network_9.cpp)]  
  
5.  添加以下代码以连接网络。  
  
     [!code-cpp[concrt-image-processing-filter#11](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-image-processing-network_10.cpp)]  
  
6.  添加以下代码以将目录中每个 [!INCLUDE[TLA#tla_jpeg](../Token/TLA%23tla_jpeg_md.md)] 文件的完整路径发送给网络头。  
  
     [!code-cpp[concrt-image-processing-filter#12](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-image-processing-network_11.cpp)]  
  
7.  等待 `countdown_event` 变量到 0。  
  
     [!code-cpp[concrt-image-processing-filter#13](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-image-processing-network_12.cpp)]  
  
 下表描述了网络中的成员。  
  
|成员|说明|  
|--------|--------|  
|`load_bitmap`|一个 [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) 对象，它从磁盘加载 `Bitmap` 对象并向 `map` 对象添加条目，以将图像与其原始文件名关联。|  
|`loaded_bitmaps`|一个 [concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md) 对象，它将加载的图像发送到图像处理筛选器。|  
|`grayscale`|一个 `transformer` 对象，它将 Tom 创作的图像转换为灰阶。  它使用图像的元数据确定图像作者。|  
|`colormask`|一个 `transformer` 对象，它将从以红色为主色的图像中删除绿色和蓝色组件。|  
|`darken`|一个 `transformer` 对象，它将调暗以红色为主色的图像。|  
|`sepiatone`|一个 `transformer` 对象，它将对不是由 Tom 创作且主色不是红色的图像应用棕褐色调。|  
|`save_bitmap`|一个 `transformer` 对象，它将处理过的 `image` 作为位图保存到磁盘。  `save_bitmap` 从 `map` 对象检索原始文件名，并将其文件扩展名更改为 .bmp。|  
|`delete_bitmap`|一个 `transformer` 对象，它释放图像的内存。|  
|`decrement`|一个 [concurrency::call](../../parallel/concrt/reference/call-class.md) 对象，它充当网络中的终端节点。  它通过递减 `countdown_event` 对象，向主应用程序传递已处理完一个图像的信号。|  
  
 `loaded_bitmaps` 消息缓冲区很重要，因为作为 `unbounded_buffer` 对象，它可将 `Bitmap` 对象提供给多个接收者。  当目标块接受 `Bitmap` 对象时，`unbounded_buffer` 对象不会再将该 `Bitmap` 对象提供给任何其他目标。  因此，您将对象链接到 `unbounded_buffer` 对象的顺序很重要。  `grayscale`、`colormask` 和 `sepiatone` 消息块都各使用一个筛选器，以便只接受特定的 `Bitmap` 对象。  `decrement` 消息缓冲区是 `loaded_bitmaps` 消息缓冲区的一个重要目标，因为它接受被其他消息缓冲区拒绝的所有 `Bitmap` 对象。  需要 `unbounded_buffer` 对象来按顺序传播消息。  因此，`unbounded_buffer` 对象会阻止操作，直到有新目标块链接到它，并且如果当前没有目标块接受该消息，它会接受该消息。  
  
 如果应用程序需要多个消息块处理该消息，而不仅仅是第一个接受该消息的消息块，则您可以使用其他消息块类型（例如 `overwrite_buffer`）。  `overwrite_buffer` 类每次容纳一条消息，但它会将该消息传播到其每个目标。  
  
 下图显示图像处理网络：  
  
 ![图像处理网络](../Image/ConcRT_ImageProc.png "ConcRT\_ImageProc")  
  
 本示例中的 `countdown_event` 对象使图像处理网络能在处理完所有图像后通知主应用程序。  `countdown_event` 类使用 [concurrency::event](../../parallel/concrt/reference/event-class.md) 对象在计数器值达到 0 时发送信号。  主应用程序每次将文件名发送到网络时都会递增计数器。  网络的终端节点在处理完每个图像后会递减计数器。  主应用程序遍历指定的目录后，它会等待 `countdown_event` 对象发送计数器已到 0 的信号。  
  
 下面的示例演示 `countdown_event` 类：  
  
 [!code-cpp[concrt-image-processing-filter#14](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-image-processing-network_13.cpp)]  
  
 \[[Top](#top)\]  
  
##  <a name="complete"></a> 完整示例  
 下面的代码显示完整的示例。  `wmain` 函数管理 [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] 库并调用 `ProcessImages` 函数，以便处理 `Sample Pictures` 目录中的 [!INCLUDE[TLA#tla_jpeg](../Token/TLA%23tla_jpeg_md.md)] 文件。  
  
 [!code-cpp[concrt-image-processing-filter#15](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-image-processing-network_14.cpp)]  
  
 下图演示示例输出。  各个源图像均位于其对应的已修改图像的上方。  
  
 ![示例的示例输出](../../parallel/concrt/media/concrt_imageout.png "ConcRT\_ImageOut")  
  
 `灯塔`由 Tom Alphin 创作，因此将其转换为灰阶。  `菊花`、`沙漠`、`考拉`和`郁金香`以红色为主色，因此删除蓝色和绿色组件并调暗。  `绣球`、`水母` 和 `企鹅` 符合默认的条件，因此转换为棕褐色调。  
  
 \[[Top](#top)\]  
  
### 编译代码  
 复制示例代码并将其粘贴到Visual Studio项目中，或者将其粘贴到名为`image-processing-network.cpp`的文件中，然后在Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/DUNICODE \/EHsc image\-processing\-network.cpp \/link gdiplus.lib**  
  
## 请参阅  
 [并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)
---
title: 演练： 创建图像处理网络 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- image-processing networks, creating [Concurrency Runtime]
- creating image-processing networks [Concurrency Runtime]
ms.assetid: 78ccadc9-5ce2-46cc-bd62-ce0f99d356b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2586a8fb15d21375ff056164d54f1f5f98891f98
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42588137"
---
# <a name="walkthrough-creating-an-image-processing-network"></a>演练：创建图像处理网络
本文档演示如何创建执行图像处理的异步消息块网络。  
  
 网络确定基于其特征对图像执行哪些操作。 此示例使用*数据流*模型通过网络路由图像。 在数据流模型中，程序的独立组件之间通过发送消息进行通信。 当某个组件收到一条消息时，它可以执行特定操作，然后将该操作的结果传递给另一个组件。 将此与比较*控制流*模型中，在其中应用程序使用控制结构，例如、 条件语句、 循环和等等，以控制在程序中的操作的顺序。  
  
 基于数据流的网络创建*管道*的任务。 在管道的每个阶段同时执行整个任务的一部分。 这就好比是汽车制造装配线。 每辆汽车通过装配线时，一站组装车架，另一个安装引擎，依次类推。 通过启用同时装配多辆汽车，程序集行提供了比一次装配整辆车拥有一个更好的吞吐量。  
  
## <a name="prerequisites"></a>系统必备  
 在开始本演练之前，请阅读以下文档：  
  
-   [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [如何：使用消息块筛选器](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
  
-   [演练：创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)  
  
 我们还建议在开始本演练之前了解 GDI + 的基础知识。  
  
##  <a name="top"></a> 部分  
 本演练包含以下各节：  
  
-   [定义图像处理功能](#functionality)  
  
-   [创建图像处理网络](#network)  
  
-   [完整示例](#complete)  
  
##  <a name="functionality"></a> 定义图像处理功能  
 本部分演示图像处理网络用来处理从磁盘读取的映像的支持函数。  
  
 以下函数`GetRGB`和`MakeColor`、 提取和分别组合给定颜色的各个组件。  
  
 [!code-cpp[concrt-image-processing-filter#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_1.cpp)]  
  

 以下函数， `ProcessImage`，调用给定[std:: function](../../standard-library/function-class.md)要转换的 GDI + 中的每个像素的颜色值对象[位图](/windows/desktop/api/gdiplusheaders/nl-gdiplusheaders-bitmap)对象。 `ProcessImage`函数使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法处理并行位图的每一行。  

  
 [!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_2.cpp)]  
  
 以下函数`Grayscale`， `Sepiatone`， `ColorMask`，和`Darken`，调用`ProcessImage`函数来转换中的每个像素的颜色值`Bitmap`对象。 每个函数使用 lambda 表达式来定义一个像素的颜色转换。  
  
 [!code-cpp[concrt-image-processing-filter#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_3.cpp)]  
  
 以下函数， `GetColorDominance`，还会调用`ProcessImage`函数。 但是，而不是更改每个颜色值，此函数使用[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)对象计算红色、 绿色还是蓝色颜色组件是否是图像。  
  
 [!code-cpp[concrt-image-processing-filter#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_4.cpp)]  
  
 以下函数， `GetEncoderClsid`，检索指定的 MIME 类型的编码器的类标识符。 应用程序使用此函数检索位图的编码器。  
  
 [!code-cpp[concrt-image-processing-filter#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_5.cpp)]  
  
 [[返回页首](#top)]  
  
##  <a name="network"></a> 创建图像处理网络  
 本部分介绍如何创建执行图像处理给定目录中每个 JPEG (.jpg) 映像的异步消息块网络。 网络执行下面的图像处理操作：  
  
1.  Tom 创作的任何图像，将转换为灰度。  
  
2.  对于任何具有主色为红色的映像，请删除对绿色和蓝色分量，然后变暗。  
  
3.  对于任何其他映像，请应用棕褐色调。  
  
 仅第一个图像处理操作之一相匹配的这些条件应用网络。 例如，如果图像作者 Tom，主要颜色为红色，映像只能转换为灰度。  
  
 网络执行每个图像处理操作后，它将图像保存到磁盘为位图 (.bmp) 文件。  
  
 以下步骤说明如何创建实现此图像处理网络并将该网络应用到给定目录中每个 JPEG 图像的函数。  
  
#### <a name="to-create-the-image-processing-network"></a>若要创建图像处理网络  
  
1.  创建一个函数， `ProcessImages`，采用在磁盘上目录的名称。  
  
     [!code-cpp[concrt-image-processing-filter#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_6.cpp)]  
  
2.  在中`ProcessImages`函数中，创建`countdown_event`变量。 `countdown_event`类稍后在本演练中所示。  
  
     [!code-cpp[concrt-image-processing-filter#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_7.cpp)]  
  
3.  创建[std:: map](../../standard-library/map-class.md)相关联的对象`Bitmap`带有其原始文件名称的对象。  
  
     [!code-cpp[concrt-image-processing-filter#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_8.cpp)]  
  
4.  添加以下代码来定义图像处理网络的成员。  
  
     [!code-cpp[concrt-image-processing-filter#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_9.cpp)]  
  
5.  添加以下代码以将网络连接。  
  
     [!code-cpp[concrt-image-processing-filter#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_10.cpp)]  
  
6.  添加以下代码将发送到网络的每个 JPEG 文件的完整路径的目录中。  
  
     [!code-cpp[concrt-image-processing-filter#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_11.cpp)]  
  
7.  等待`countdown_event`变量归零。  
  
     [!code-cpp[concrt-image-processing-filter#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_12.cpp)]  
  
 下表描述了网络的成员。  
  
|成员|描述|  
|------------|-----------------|  
|`load_bitmap`|一个[concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)对象，它将加载`Bitmap`从磁盘对象，并添加一个条目`map`对象以将图像与其原始文件名与相关联。|  
|`loaded_bitmaps`|一个[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)将加载的图像发送到图像处理筛选器的对象。|  
|`grayscale`|一个`transformer`对象，它将转换为灰度作者 Tom 的映像。 它使用的图像的元数据来确定它的作者。|  
|`colormask`|一个`transformer`绿色和蓝色分量解除对主色为红色的图像的对象。|  
|`darken`|一个`transformer`会变暗红色主流色的映像的对象。|  
|`sepiatone`|一个`transformer`适用棕褐色调到不由 Tom 创作，而不是红色的映像的对象。|  
|`save_bitmap`|一个`transformer`保存已处理对象`image`到磁盘作为位图。 `save_bitmap` 检索从原始文件名`map`对象，并更改其文件扩展名为.bmp。|  
|`delete_bitmap`|一个`transformer`释放的图像的内存的对象。|  
|`decrement`|一个[concurrency:: call](../../parallel/concrt/reference/call-class.md)充当网络中的终端节点的对象。 它递减`countdown_event`将信号发送到主应用程序映像已处理的对象。|  
  
 `loaded_bitmaps`消息缓冲区很重要，因为作为`unbounded_buffer`对象，它提供了`Bitmap`到多个接收方对象。 当目标块接受`Bitmap`对象，`unbounded_buffer`对象不提供`Bitmap`到任何其他目标的对象。 因此，在该链接的顺序对象添加到`unbounded_buffer`对象很重要。 `grayscale`， `colormask`，并`sepiatone`每个块使用筛选器来接受消息只有某些特定`Bitmap`对象。 `decrement`消息缓冲区是重要的目标`loaded_bitmaps`因为它接受所有消息缓冲区`Bitmap`拒绝的其他消息缓冲区的对象。 `unbounded_buffer`传播消息按顺序所需的对象。 因此，`unbounded_buffer`对象被阻止，直至新的目标块链接到它，并接受消息，如果没有当前的目标块接受此消息。  
  
 如果应用程序需要多个消息块处理该消息，而不是只是一条消息块的第一个接受消息，你可以使用另一个消息块类型，如`overwrite_buffer`。 `overwrite_buffer`类包含一条消息一次，但它可传播到其每个目标的消息。  
  
 下图显示了图像处理网络：  
  
 ![图像处理网络](../../parallel/concrt/media/concrt_imageproc.png "concrt_imageproc")  
  
 `countdown_event`对象在此示例中，图像处理网络来通知主应用程序时已处理的所有映像。 `countdown_event`类使用[concurrency:: event](../../parallel/concrt/reference/event-class.md)对象时的计数器值达到零时发出信号通知。 主应用程序每次它发送到网络的文件名称时递增的计数器。 网络递减的终端节点处理的每个图像后的计数器。 主应用程序会遍历指定的目录后，它将等待`countdown_event`对象发出信号的计数器归零。  
  
 下面的示例演示`countdown_event`类：  
  
 [!code-cpp[concrt-image-processing-filter#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_13.cpp)]  
  
 [[返回页首](#top)]  
  
##  <a name="complete"></a> 完整示例  
 以下代码显示完整示例。 `wmain`函数管理 GDI + 库，然后调用`ProcessImages`中的函数来处理 JPEG 文件`Sample Pictures`目录。  
  
 [!code-cpp[concrt-image-processing-filter#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_14.cpp)]  
  
 下图显示了示例输出。 每个源映像高于其相应的修改后的映像。  
  
 ![该示例的输出示例](../../parallel/concrt/media/concrt_imageout.png "concrt_imageout")  
  
 `Lighthouse` 通过 Tom Alphin 创作的因此将转换为灰度。 `Chrysanthemum``Desert`， `Koala`，和`Tulips`红色主流色因此删除了蓝色和绿色颜色组件并调暗。 `Hydrangeas``Jellyfish`，和`Penguins`与默认条件匹配，因此转换为棕褐色。  
  
 [[返回页首](#top)]  
  
### <a name="compiling-the-code"></a>编译代码  
 复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`image-processing-network.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /DUNICODE /EHsc 图像处理 network.cpp /link gdiplus.lib**  
  
## <a name="see-also"></a>请参阅  
 [并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)

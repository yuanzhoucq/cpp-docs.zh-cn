---
title: 如何：在数据管道中使用转换器
ms.date: 11/04/2016
helpviewer_keywords:
- transformer class, example
- data pipelines, using transformer [Concurrency Runtime]
- using transformer in data pipelines [Concurrency Runtime]
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
ms.openlocfilehash: 59c4854eea985b3c91fad6e7dc6c47ca9b07d333
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375582"
---
# <a name="how-to-use-transformer-in-a-data-pipeline"></a>如何：在数据管道中使用转换器

本主题包含演示如何使用一个基本示例[concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)数据管道中的类。 使用数据管道来执行图像处理的更完整示例，请参阅[演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。

*数据管道*是并发编程中的常见模式。 数据管道由一系列的阶段，其中每个阶段执行工作，然后将该工作的结果传递给下一个阶段组成。 `transformer`类数据中的关键组件管道，因为它接收输入的值，该值，对执行工作，然后生成另一个组件使用的结果。

## <a name="example"></a>示例

此示例使用以下数据管道中执行的一系列转换给定的初始输入的值：

1. 第一阶段计算其输入的绝对值。

1. 第二个阶段计算其输入的平方根。

1. 第三个阶段计算其输入的平方。

1. 规定阶段对其输入的求反。

1. 第五个阶段将最终结果写入到消息缓冲区。

最后，该示例将打印到控制台管道的结果。

[!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/cpp/how-to-use-transformer-in-a-data-pipeline_1.cpp)]

该示例产生下面的输出：

```Output
The result is -42.
```

用于输出的值的类型不同于其输入值的数据管道中的阶段很常见。 在此示例中，第二个阶段所用的类型的值`int`作为其输入，并生成此值的平方根 ( `double`) 作为其输出。

> [!NOTE]
>  此示例中的数据管道是为了进行说明。 由于每个转换操作执行一些工作，因此开销，它是需要执行消息传递可以大于使用的数据管道的好处。

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`data-pipeline.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc data-pipeline.cpp**

## <a name="see-also"></a>请参阅

[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)

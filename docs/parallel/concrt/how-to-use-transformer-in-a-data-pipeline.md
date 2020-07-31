---
title: 如何：在数据管道中使用转换器
ms.date: 11/04/2016
helpviewer_keywords:
- transformer class, example
- data pipelines, using transformer [Concurrency Runtime]
- using transformer in data pipelines [Concurrency Runtime]
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
ms.openlocfilehash: 4eb490ecf51abea324f20395279bff2d74b7af77
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215850"
---
# <a name="how-to-use-transformer-in-a-data-pipeline"></a>如何：在数据管道中使用转换器

本主题包含一个示例，该示例演示如何在数据管道中使用[concurrency：：转换器](../../parallel/concrt/reference/transformer-class.md)类。 有关使用数据管道执行图像处理的更完整示例，请参阅[演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。

*数据流水线*是并发编程中的一种常见模式。 数据管道由一系列阶段组成，其中每个阶段都执行工作，然后将该工作的结果传递到下一个阶段。 `transformer`类是数据管道中的一个关键组件，因为它接收输入值，对该值执行工作，然后生成另一个要使用的组件的结果。

## <a name="example"></a>示例

此示例使用以下数据管道在给定初始输入值的情况下执行一系列转换：

1. 第一个阶段计算其输入的绝对值。

1. 第二个阶段计算其输入的平方根。

1. 第三个阶段计算其输入的平方。

1. 向后阶段将对其输入求反。

1. 第五个阶段将最终结果写入消息缓冲区。

最后，此示例将管道的结果输出到控制台。

[!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/cpp/how-to-use-transformer-in-a-data-pipeline_1.cpp)]

该示例产生下面的输出：

```Output
The result is -42.
```

数据管道中的阶段通常会输出其类型与其输入值不同的值。 在此示例中，第二个阶段将类型的值 **`int`** 作为其输入，并生成该值的平方根（a **`double`** ）作为其输出。

> [!NOTE]
> 本示例中的数据管道用于说明。 由于每个转换操作执行的操作很少，因此执行消息传递所需的开销可能会超过使用数据管道的好处。

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为的文件中， `data-pipeline.cpp` 然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl.exe/EHsc data-pipeline**

## <a name="see-also"></a>另请参阅

[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)

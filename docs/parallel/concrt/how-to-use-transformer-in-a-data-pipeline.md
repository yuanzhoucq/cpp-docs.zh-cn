---
title: "如何： 在数据管道中的使用 transformer |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- transformer class, example
- data pipelines, using transformer [Concurrency Runtime]
- using transformer in data pipelines [Concurrency Runtime]
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 76c8a50bd5a58d9fe6e4a68f05d9732e50fd04e8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-transformer-in-a-data-pipeline"></a>如何：在数据管道中使用转换器
本主题包含演示如何使用一个基本示例[concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)在数据管道中的类。 有关使用数据管道来执行图像处理的更完整示例，请参阅[演练： 创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。  
  
 *数据管道*是在并发编程的通用模式。 数据管道包含一系列的阶段，其中每个阶段执行工作，然后将该工作的结果传递给下一个阶段。 `transformer`类管道中数据的关键组成部分，因为它接收输入的值，该值，对执行工作，然后生成另一个组件使用的结果。  
  
## <a name="example"></a>示例  
 此示例使用以下数据管道执行一系列转换给定的初始输入的值：  
  
1.  第一阶段计算其输入的绝对值。  
  
2.  第二个阶段计算其输入的平方根。  
  
3.  第三个阶段计算其输入的平方。  
  
4.  阶段规定对其输入求反。  
  
5.  第五个阶段写入消息缓冲区的最终结果。  
  
 最后，示例输出到控制台管道的结果。  
  
 [!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/cpp/how-to-use-transformer-in-a-data-pipeline_1.cpp)]  
  
 该示例产生下面的输出：  
  
```Output  
The result is -42.  
```  
  
 在数据管道输出其类型不同于其输入值的值中的一阶段很常见。 在此示例中，第二个阶段采用类型的值`int`作为其输入，并生成该值的平方根 ( `double`) 作为其输出。  
  
> [!NOTE]
>  在此示例中数据管道是为了进行说明。 因为每个转换操作执行少量工作，开销，它是需要执行消息传递可以带来的好处的使用数据管道。  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`data-pipeline.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc data-pipeline.cpp**  
  
## <a name="see-also"></a>请参阅  
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)   
 [演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)


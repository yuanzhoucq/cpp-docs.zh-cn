---
title: "如何：在数据管道中使用转换器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "transformer 类，示例"
  - "数据管线，使用转换器 [并发运行时]"
  - "在数据管线中使用转换器 [并发运行时]"
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 如何：在数据管道中使用转换器
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题包含一个基本示例，该示例演示如何在数据管道中使用 [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) 类。  有关使用数据管道执行图像处理操作的更完整示例，请参见[演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。  
  
 “数据管道”是并发编程中的常见模式。  数据管道由一系列阶段组成，其中每个阶段执行工作，然后将该工作的结果传递到下一阶段。  `transformer` 类是数据管道中的一个关键组件，因为它接收输入值，对该值进行处理，然后生成供另一个组件使用的结果。  
  
## 示例  
 该示例使用以下数据管道执行一系列的给定初始输入值的转换：  
  
1.  第一个阶段计算其输入的绝对值。  
  
2.  第二个阶段计算其输入的平方根。  
  
3.  第三个阶段计算其输入的平方。  
  
4.  第四个阶段对其输入求反。  
  
5.  第五个阶段将最终结果写入消息缓冲区。  
  
 最后，该示例将管道的结果输出到控制台。  
  
 [!CODE [concrt-data-pipeline#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-data-pipeline#1)]  
  
 该示例产生下面的输出：  
  
  **结果为 \-42。** 数据管道中的阶段通常输出一个其类型不同于输入值类型的值。  在该示例中，第二个阶段采用 `int` 类型的值作为其输入值，并生成该值的平方根 \(`double`\) 作为其输出。  
  
> [!NOTE]
>  此示例中的数据管道用于说明。  因为每项转换操作都很少工作，所以执行消息传递任务所需的开销会超过使用数据管道带来的好处。  
  
## 编译代码  
 复制代码示例，再将此代码粘贴到Visual Studio 项目中或一个名为 `data-pipeline.cpp` 的文件中，然后在 Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc data\-pipeline.cpp**  
  
## 请参阅  
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)   
 [演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)
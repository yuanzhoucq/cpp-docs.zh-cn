---
title: "异常：从您自己的函数引发异常 | Microsoft Docs"
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
  - "异常, 引发"
  - "函数 [C++], 引发异常"
  - "引发异常, 从函数"
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 异常：从您自己的函数引发异常
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用异常本身处理示例捕捉 MFC 或其他库中的函数引发的异常是可能的。  除了捕获库代码引发异常之外，如果您编写的函数可以遇到异常条件，您可以在您自己的代码中抛出异常。  
  
 在异常引发时，当前函数的执行停止并直接跳转到最内层的异常框架的 **catch** 块。  异常机制跳过从函数退出的正常路径。  因此，必须确保删除处于正常退出将删除的那些存储区。  
  
#### 抛出异常  
  
1.  使用一个 MFC 的帮助程序函数，例如 `AfxThrowMemoryException`。  这些函数引发适当类型的预分配的异常对象。  
  
     在下面示例中，函数尝试分配两个存储区，如果任何一个分配失败则引发异常：  
  
     [!code-cpp[NVC_MFCExceptions#17](../mfc/codesnippet/CPP/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]  
  
     如果第一个分配失败，您可以简单抛出内存异常。  如果第一个分配成功，但第二个失败，则必须在抛出异常之前释放第一次分配的块。  如果两这都分配成功，通常可以正常运行，当退出函数时释放块。  
  
     \- 或 \-  
  
2.  使用用户定义的异常指示问题情况。  可以抛出任何类型项，甚至整个类，按您的意愿。  
  
     以下示例尝试通过波形设备播放声音，如果失败则抛出异常。  
  
     [!code-cpp[NVC_MFCExceptions#18](../mfc/codesnippet/CPP/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]  
  
> [!NOTE]
>  MFC 的默认异常处理仅适用于指向 `CException` 对象 的指针\( 以及 `CException` 派生类的对象。\)  上面的例子跳过 MFC 的异常机制。  
  
## 请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)
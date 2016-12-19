---
title: "异常：检查异常内容 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "捕捉块, MFC 函数异常"
  - "CException 类, 类异常"
  - "异常处理, MFC"
  - "引发异常, 异常内容"
  - "try-catch 异常处理, 异常内容"
  - "try-catch 异常处理, MFC 函数异常"
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 异常：检查异常内容
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

虽然 **catch** 块的参数可以为几乎任何数据类型，MFC 函数引发从类派生类型的异常的 `CException`。  为了捕捉 MFC 函数引发的异常，然后，编写参数是指向 `CException` 对象的 **catch** 块 \(或从 `CException`派生的对象，如 `CMemoryException`\)。  根据异常的确切类型，您可以检查异常对象的数据成员。收集信息的异常信息的特定原因。  
  
 例如，`CFileException` 类型具有 `m_cause` 数据成员，包含一枚举类型指定文件异常的原因。  可以返回值的一些示例包括 **CFileException::fileNotFound** 和 **CFileException::readOnly**。  
  
 下面的示例演示如何检查 `CFileException`的内容。  其他异常类型可能类似进行检查。  
  
 [!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/CPP/exceptions-examining-exception-contents_1.cpp)]  
  
 有关更多信息，请参见 [异常：版本在异常对象](../mfc/exceptions-freeing-objects-in-exceptions.md) 和 [异常：捕获异常和删除](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
## 请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)
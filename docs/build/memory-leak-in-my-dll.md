---
title: "规则 DLL 中有内存泄漏，但代码看起来很正常。 如何找到内存泄漏？ | Microsoft Docs"
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
  - "DLL [C++], 内存泄漏"
  - "内存泄漏 [C++], DLL"
ms.assetid: a5d76573-b567-4b6a-8303-dafeeed9204d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 规则 DLL 中有内存泄漏，但代码看起来很正常。 如何找到内存泄漏？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

引起内存泄漏的一个可能原因是 MFC 创建了在消息处理函数内使用的临时对象。  在规则 DLL 中，MFC 不自动释放分配给这些对象的内存。  有关更多信息，请参见[内存管理和调试堆](http://msdn.microsoft.com/zh-cn/34dc6ef6-31c9-460e-a2a7-15e7f8e3334b)或知识库文章“Cleaning Up Temporary MFC Objects in \_USRDLL DLLs”\(Q105286\)。  
  
 请注意，Visual C\+\+ 文档中不再使用 USRDLL 一词。  静态链接到 MFC 的规则 DLL 具有与原来的 USRDLL 相同的特性。  知识库文章中的建议同样适用于动态链接到 MFC 的规则 DLL。  上述知识库文章中的信息既适用于静态链接到 MFC 的规则 DLL，也适用于动态链接到 MFC 的规则 DLL。  
  
## 请参阅  
 [DLL 常见问题](../build/dll-frequently-asked-questions.md)
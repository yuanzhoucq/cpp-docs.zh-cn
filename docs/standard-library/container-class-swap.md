---
title: "Container Class::swap | Microsoft Docs"
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
  - "swap 方法"
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Container Class::swap
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  本主题介绍 Visual C\+\+ 文档作为使用标准 C\+\+ 库的容器的非运行的示例。  有关更多信息，请参见 [STL 容器](../standard-library/stl-containers.md)。  
  
 交换。**\*this** 和 `_Right`的顺序控制。  
  
## 语法  
  
```  
  
      void swap(  
   Container& _Right  
);  
```  
  
## 备注  
 如果 **get\_allocator \=\=** `_Right`**.get\_allocator**，将常数的时间执行。  否则，它将执行大量的元素赋值，然后构造函数调用而与元素数目在两个控件的顺序。  
  
## 请参阅  
 [Sample Container 类](../standard-library/sample-container-class.md)
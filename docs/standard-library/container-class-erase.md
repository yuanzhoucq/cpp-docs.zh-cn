---
title: "Container Class::erase | Microsoft Docs"
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
  - "erase 方法"
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Container Class::erase
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  本主题介绍 Visual C\+\+ 文档作为使用标准 C\+\+ 库的容器的非运行的示例。  有关更多信息，请参见 [STL 容器](../standard-library/stl-containers.md)。  
  
 擦除元素。  
  
## 语法  
  
```  
  
      iterator erase(  
   iterator _Where   
);  
iterator erase(  
   iterator _First,  
   iterator _Last   
);  
```  
  
## 备注  
 第一移除成员函数控制序列的元素指向由\_Where \#\#\#.第二个成员函数移除控制序列的元素处于范围 \[`_First`，`_Last`\)。  返回两指定保留超过所有元素外的第一个元素。移除的迭代器或 [结束时间](../standard-library/container-class-end.md)，如果不存在这样的元素。  
  
 仅复制操作引发异常，则成员函数将引发异常。  
  
## 请参阅  
 [Sample Container 类](../standard-library/sample-container-class.md)
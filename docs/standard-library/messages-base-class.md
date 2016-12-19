---
title: "messages_base 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.messages_base"
  - "messages_base"
  - "std::messages_base"
  - "locale/std::messages_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "messages_base 类"
ms.assetid: 9aad38c6-4c13-445d-b096-364bd0836efb
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# messages_base 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

基类介绍消息目录的 `int` 类型。  
  
## 语法  
  
```  
struct messages_base : locale::facet {  
    typedef int catalog;  
    explicit messages_base(size_t _Refs = 0)  
};  
```  
  
## 备注  
 目录类型是可从[do\_open](../Topic/messages::do_open.md)messages:: 的返回值类型的 `int` 的同义词。  
  
## 要求  
 **页眉：** \<区域设置\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
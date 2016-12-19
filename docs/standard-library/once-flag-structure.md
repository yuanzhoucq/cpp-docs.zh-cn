---
title: "once_flag 结构 | Microsoft Docs"
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
  - "mutex/std::once_flag"
dev_langs: 
  - "C++"
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# once_flag 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示 `struct` 用模板函数 [call\_once](../Topic/call_once%20Function.md) 甚至在出现之前执行多线程确保初始化的代码仅调用一次。，  
  
## 语法  
  
```cpp  
struct once_flag  
{  
   constexpr once_flag() noexcept;  
   once_flag(const once_flag&);  
   once_flag& operator=(const once_flag&);  
};  
```  
  
## 备注  
 `once_flag` `struct` 仅具有一个默认构造函数。  
  
 `once_flag` 类型的对象，可以创建，但不可复制。  
  
## 要求  
 **标头:** mutex  
  
 **命名空间:** std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)
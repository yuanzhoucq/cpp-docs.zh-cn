---
title: "在没有构造函数的情况下初始化类和结构 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在没有构造函数的情况下初始化类和结构 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

并不总是需要为类定义构造函数，特别是相对比较简单的类。  用户可以使用统一初始化来初始化类或结构的对象，如下面的示例所示：  
  
```  
struct TempData  
{  
    int StationId;  
    time_t time;  
    double current;  
    double max;  
    double min;  
};  
  
int _tmain(int argc, _TCHAR* argv[])  
{  
    // Member initialization:  
    TempData td { 45978, GetCurrentTime(), 28.9, 37.0, 16.7 };  
  
    // Default initialization = {0,0,0,0,0}  
    TempData td_default {};  
  
    //Error C4700 uninitialized local variable  
    TempData td_noInit;   
    return 0;  
}  
```  
  
## 请参阅  
 [类和结构](../cpp/classes-and-structs-cpp.md)   
 [构造函数](../cpp/constructors-cpp.md)
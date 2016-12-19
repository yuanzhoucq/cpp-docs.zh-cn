---
title: "time_base 类 | Microsoft Docs"
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
  - "std.time_base"
  - "std::time_base"
  - "time_base"
  - "locale/std::time_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "time_base 类"
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# time_base 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

类用作基类对象的 time\_get 个模板类，定义枚举类型 **dateorder**，并且此的常数多个类型。  
  
## 语法  
  
```  
class time_base : public locale::facet {  
public:  
    enum dateorder {no_order, dmy, mdy, ymd, ydm};  
    time_base(  
        size_t _Refs = 0  
    )  
    ~time_base();  
};  
```  
  
## 备注  
 每个常量分析不同的方式对日期的组件。  常数是：  
  
-   **no\_order** 未指定特定顺序。  
  
-   **dmy** 在 1979 年 12 月 2 日指定排序日，月份，然后，年。  
  
-   **mdy** 在 1979 年 12 月 2 日，月份日，再指定排序，年。  
  
-   **ymd** 在 1979\/12\/2. 指定排序年，日，月份，然后。  
  
-   **ydm** 在 1979 年中指定排序，日，月份，然后：12 月 2 日。  
  
## 要求  
 **页眉：** \<区域设置\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
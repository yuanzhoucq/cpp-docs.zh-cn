---
title: "计算所需值 | Microsoft Docs"
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
  - "Helper 函数, 计算所需值"
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 计算所需值
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

延迟 Helper 例程需要计算两条重要信息。  为实现该目标，delayhlp.cpp 中有两个内联函数用于计算此信息。  
  
-   第一个函数计算三个不同表（导入地址表 \(IAT\)、绑定导入地址表 \(BIAT\) 和未绑定导入地址表 \(UIAT\)）中的当前导入的索引。  
  
-   第二个对有效 IAT 中的导入的数目进行计数。  
  
```  
// utility function for calculating the index of the current import  
// for all the tables (INT, BIAT, UIAT, and IAT).  
__inline unsigned  
IndexFromPImgThunkData(PCImgThunkData pitdCur, PCImgThunkData pitdBase) {  
    return pitdCur - pitdBase;  
    }  
  
// utility function for calculating the count of imports given the base  
// of the IAT. NB: this only works on a valid IAT!  
__inline unsigned  
CountOfImports(PCImgThunkData pitdBase) {  
    unsigned        cRet = 0;  
    PCImgThunkData  pitd = pitdBase;  
    while (pitd->u1.Function) {  
        pitd++;  
        cRet++;  
        }  
    return cRet;  
    }  
```  
  
## 请参阅  
 [Understanding the Helper Function](http://msdn.microsoft.com/zh-cn/6279c12c-d908-4967-b0b3-cabfc3e91d3d)
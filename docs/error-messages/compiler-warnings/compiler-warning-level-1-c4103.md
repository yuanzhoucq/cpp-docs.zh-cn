---
title: "编译器警告（等级 1）C4103 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4103"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4103"
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4103
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“filename”: 在包含头后更改了对齐方式，可能是由于缺少 \#pragma pack\(pop\)  
  
 封装影响类的布局，并且如果封装在各个头文件中有所更改，则通常会有问题。  
  
 退出头文件前使用 \#pragma [pack](../../preprocessor/pack.md)\(pop\) 可解决此警告。  
  
 下面的示例生成 C4103：  
  
```  
// C4103.h  
#pragma pack(push, 4)  
  
// defintions and declarations  
  
// uncomment the following line to resolve  
// #pragma pack(pop)  
```  
  
 然后，  
  
```  
// C4103.cpp  
// compile with: /LD /W1  
#include "c4103.h"   // C4103  
```
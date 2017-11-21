---
title: "编译器警告 （等级 1） C4103 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4103
dev_langs: C++
helpviewer_keywords: C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1ac53a33d64bede8351d3b981b9c2a7e324e3f1f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4103"></a>编译器警告 （等级 1） C4103
filename： 包含标头后, 更改的对齐方式可能是由于缺少 #pragma pack(pop)  
  
 封装影响布局的类，并且通常情况下，如果封装在标头文件之间的更改，可能会有问题。  
  
 使用 #pragma[包](../../preprocessor/pack.md)(pop) 之前退出标头文件，若要解决此警告。  
  
 下面的示例生成 C4103:  
  
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
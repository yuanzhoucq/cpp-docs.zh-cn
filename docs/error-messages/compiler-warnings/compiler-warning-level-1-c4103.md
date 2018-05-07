---
title: 编译器警告 （等级 1） C4103 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4103
dev_langs:
- C++
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f072db4a260d2c83d1dd4b373630cd6e585efc2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
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
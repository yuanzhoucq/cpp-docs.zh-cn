---
title: 编译器警告 （等级 1） C4163 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4163
dev_langs:
- C++
helpviewer_keywords:
- C4163
ms.assetid: b08413fd-03fc-4f41-9167-a98976ac12f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d39297a17c5e7c7b6b95fd0e43f33849c092fa1d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275536"
---
# <a name="compiler-warning-level-1-c4163"></a>编译器警告（等级 1）C4163
“identifier”：不可用作内部函数  
  
 指定的函数不能用作 [intrinsic](../../preprocessor/intrinsic.md) 函数。 编译器将忽略无效的函数名称。  
  
 以下示例生成 C4163：  
  
```  
// C4163.cpp  
// compile with: /W1 /LD  
#include <math.h>  
#pragma intrinsic(mysin)   // C4163  
// try the following line instead  
// #pragma intrinsic(sin)  
```
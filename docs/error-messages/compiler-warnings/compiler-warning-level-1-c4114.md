---
title: 编译器警告 （等级 1） C4114 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4114
dev_langs:
- C++
helpviewer_keywords:
- C4114
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78402d4487eecde00c55ea5e0aad913d97226325
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283918"
---
# <a name="compiler-warning-level-1-c4114"></a>编译器警告 （等级 1） C4114
多次使用同一类型限定符  
  
 类型声明或定义使用的类型限定符 (**const**， `volatile`，**签名**，或`unsigned`) 不止一次。 这会导致具有 Microsoft 扩展 (/Ze) 警告而是在 ANSI 兼容性 (/Za) 下的错误。  
  
 下面的示例生成 C4114:  
  
```  
// C4114.cpp  
// compile with: /W1 /c  
volatile volatile int i;   // C4114  
```  
  
 下面的示例生成 C4114:  
  
```  
// C4114_b.cpp  
// compile with: /W1 /c  
static const int const * ii;   // C4114  
static const int * const iii;   // OK  
```
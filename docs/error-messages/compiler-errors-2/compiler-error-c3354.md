---
title: 编译器错误 C3354 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3354
dev_langs:
- C++
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b4bcc36580a453932068350f01b53c5f09f2d69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257349"
---
# <a name="compiler-error-c3354"></a>编译器错误 C3354
“%$I”：该函数用于创建不能有返回类型“type”的委托  
  
 以下类型作为 `delegate`的返回类型无效：  
  
-   指向函数的指针  
  
-   指向成员的指针  
  
-   指向成员函数的指针  
  
-   对函数的引用  
  
-   对成员函数的引用  
  
 以下示例生成 C3354：  
  
```  
// C3354_2.cpp  
// compile with: /clr /c  
using namespace System;  
typedef void ( *VoidPfn )();  
  
delegate VoidPfn func(); // C3354  
// try the following line instead  
// delegate  void func();  
```  

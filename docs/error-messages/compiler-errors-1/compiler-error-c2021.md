---
title: 编译器错误 C2021 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2021
dev_langs:
- C++
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae1c3640b4fbe5b1473c2e678406321f5533e586
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167497"
---
# <a name="compiler-error-c2021"></a>编译器错误 C2021
应输入指数值而非“character”  
  
 用作浮点常数的指数的字符不是有效的数字。 请务必使用在范围内的指数。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2021:  
  
```  
// C2021.cpp  
float test1=1.175494351E;   // C2021  
```  
  
## <a name="example"></a>示例  
 可能的解决方法：  
  
```  
// C2021b.cpp  
// compile with: /c  
float test2=1.175494351E8;  
```
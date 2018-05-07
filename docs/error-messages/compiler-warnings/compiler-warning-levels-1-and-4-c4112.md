---
title: 编译器警告 （等级 1 和 4） C4112 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4112
dev_langs:
- C++
helpviewer_keywords:
- C4112
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43718511af0d85f0c9026fe70b4749c4e3d4b1e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-levels-1-and-4-c4112"></a>编译器警告（等级 1 和等级 4）C4112
\#行需要介于 1 到 number 之间的整数  
  
 [#line](../../preprocessor/hash-line-directive-c-cpp.md) 指令指定了一个位于允许范围之外的整数参数。  
  
 若指定的参数小于 1，则行计数器将重置为 1。 如果指定的参数大于 *number*，即编译器定义的限制，则行计数器保持不变。 这是在 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 下的第 1 级警告和 Microsoft 扩展 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))下的第 4 级警告。  
  
 下面的示例生成 C4112：  
  
```  
// C4112.cpp  
// compile with: /W4  
#line 0   // C4112, value must be between 1 and number  
  
int main() {  
}  
```
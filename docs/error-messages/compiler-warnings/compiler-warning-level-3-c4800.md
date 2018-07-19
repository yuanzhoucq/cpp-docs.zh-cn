---
title: 编译器警告 （等级 3） C4800 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4800
dev_langs:
- C++
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed4b14ae2f3af3218909d6cd4609f1f45d3d7cc2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293629"
---
# <a name="compiler-warning-level-3-c4800"></a>编译器警告（等级 3）C4800  
  
> *类型*: bool 'true' 或 'false' （性能警告） 到强制值  
  
值时，不会生成此警告`bool`分配或强制转换为类型`bool`。 通常情况下，此消息由分配`int`到变量`bool`变量其中`int`变量仅包含值**true**和**false**，并且可能重新声明为类型`bool`。 如果你不能重写要使用类型的表达式`bool`，然后可以将添加"`!=0`"到表达式中，它会为提供的表达式类型`bool`。 强制转换表达式类型`bool`不会禁用警告，这是设计使然。  
  
在 Visual Studio 2017 不再生成此警告。  
  
## <a name="example"></a>示例
  
 下面的示例生成 C4800，并演示如何修复此错误：  
  
```cpp  
// C4800.cpp  
// compile with: /W3  
int main() {  
   int i = 0;  
  
   // To fix, instead try:  
   // bool i = 0;  
  
   bool j = i;   // C4800  
   j++;  
}  
```
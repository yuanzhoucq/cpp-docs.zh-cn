---
title: "编译器警告 （等级 3） C4800 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4800
dev_langs:
- C++
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 687b0dab996bfbfe2ce30d65b86196383c02b914
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
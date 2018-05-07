---
title: 编译器错误 C3532 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3532
dev_langs:
- C++
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1efce6659f8d848b47f0c4194b6420177ffad194
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3532"></a>编译器错误 C3532
type: auto 用法不正确  
  
 指明的类型不能用声明`auto`关键字。 例如，不能使用`auto`关键字来声明一个数组或方法返回类型。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  确保初始化表达式结果是有效类型。  
  
2.  确保不要声明数组或方法的返回类型。  
  
## <a name="example"></a>示例  
 下面的示例会产生 C3532，因为`auto`关键字不能声明方法的返回类型。  
  
```  
// C3532a.cpp  
// Compile with /Zc:auto  
auto f(){}   // C3532  
```  
  
## <a name="example"></a>示例  
 下面的示例会产生 C3532，因为`auto`关键字不能声明数组。  
  
```  
// C3532b.cpp  
// Compile with /Zc:auto  
int main()  
{  
   int x[5];  
   auto a[5];            // C3532  
   auto b[1][2];         // C3532  
   auto y[5] = x;        // C3532  
   auto z[] = {1, 2, 3}; // C3532  
   auto w[] = x;         // C3532  
   return 0;  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)
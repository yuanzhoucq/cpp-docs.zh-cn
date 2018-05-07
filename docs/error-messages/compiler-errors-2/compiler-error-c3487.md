---
title: 编译器错误 C3487 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3487
dev_langs:
- C++
helpviewer_keywords:
- C3487
ms.assetid: 39bda474-4418-4a79-98bf-2b22fa92eaaa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb30b9a2cb0b77eff0888da6c387bd3b06182721
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3487"></a>编译器错误 C3487
“返回类型”: 所有返回表达式必须推导为相同类型: 以前为“返回类型”  
  
 Lambda 必须指定其返回类型，除非它包含单个返回语句。 如果 lambda 包含多个返回语句，则它们必须具有相同类型。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   为 lambda 指定结尾返回类型。 验证 lambda 的所有返回值都属于相同类型或可以隐式转换为返回类型。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3487，因为 lambda 的返回类型不匹配：  
  
```  
// C3487.cpp  
// Compile by using: cl /c /W4 C3487.cpp  
  
int* test(int* pi) {  
   // To fix the error, uncomment the trailing return type below  
   auto odd_pointer = [=]() /* -> int* */ {  
      if (*pi % 2)   
         return pi;  
      return nullptr; // C3487 - nullptr is not an int* type  
   };  
   return odd_pointer();  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)
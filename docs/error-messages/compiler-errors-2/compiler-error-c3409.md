---
title: 编译器错误 C3409 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3409
dev_langs:
- C++
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1964cffd0593e87a790befd8a76ae13847f2058d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3409"></a>编译器错误 C3409
不允许空特性块  
  
 方括号被解释为编译器[属性](../../windows/cpp-attributes-reference.md)找到块，但没有属性。  
  
 当你使用方括号的 lambda 表达式定义的一部分时，编译器可能生成此错误。 当编译器无法确定方括号是否定义或特性块的 lambda 表达式的一部分时，将出现此错误。 有关 lambda 表达式的详细信息，请参阅 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  如果方括号特性块的一部分：  
  
    1.  提供的属性块中的一个或多个属性。  
  
    2.  删除该特性块。  
  
2.  如果方括号是 lambda 表达式的一部分：  
  
    1.  请确保在 lambda 表达式遵循有效语法规则。  
  
         有关 lambda 表达式语法的详细信息，请参阅[Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)。  
  
    2.  
  
## <a name="example"></a>示例  
 下面的示例生成 C3409。  
  
```  
// C3409.cpp  
// compile with: /c  
#include <windows.h>  
[]   // C3409  
class a {};  
  
// OK  
[object, uuid("00000000-0000-0000-0000-000000000000")]  
__interface x {};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000001")]  
class b : public x {};  
```  
  
## <a name="example"></a>示例  
 下面的示例生成 C3409，因为 lambda 表达式使用`mutable`规范中，但未提供参数列表。 编译器无法确定方括号是否定义或特性块的 lambda 表达式的一部分。  
  
```  
// C3409b.cpp  
  
int main()  
{  
   [] mutable {}();  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [属性](../../windows/cpp-attributes-reference.md)   
 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)   
 [Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)
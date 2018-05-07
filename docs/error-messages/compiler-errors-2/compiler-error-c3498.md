---
title: 编译器错误 C3498 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3498
dev_langs:
- C++
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 913caa8fc73e5fe325a9d17a48b6c2b9ba641546
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3498"></a>编译器错误 C3498
var： 无法捕获具有托管的变量或 WinRTtype  
  
 无法在 lambda 中捕获具有托管类型或 Windows 运行时类型的变量。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   将托管或 Windows 运行时变量传递到 lambda 表达式的参数列表。  
  
## <a name="example"></a>示例  
 下面的示例将生成 C3498，因为 lambda 表达式的捕获列表中出现了具有托管类型的变量：  
  
```  
// C3498a.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String ^ s = "Hello";  
   [&s](String ^ r)   
      { return String::Concat(s, r); } (", World!"); // C3498  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例通过将托管变量 `s` 传递到 lambda 表达式的参数列表，解决了 C3498：  
  
```  
// C3498b.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String ^ s = "Hello";  
   [](String ^ s, String ^ r)   
      { return String::Concat(s, r); } (s, ", World!");  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)
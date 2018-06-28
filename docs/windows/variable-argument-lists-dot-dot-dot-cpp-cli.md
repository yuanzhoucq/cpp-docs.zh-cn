---
title: 变量自变量列表 （...）(C + + /CLI CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eec0e3591da2417137fda3bae4ed9e7860472fb2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889818"
---
# <a name="variable-argument-lists--ccli"></a>变量自变量列表 (...) (C++/CLI)
此示例演示如何使用`...`Visual c + +，以实现具有可变数量的自变量的函数的语法。  
  
> [!NOTE]
>  本主题适用于 C + + /cli CLI。 有关使用信息`...`ISO 标准 c + + 中，请参阅[省略号和可变参数模板](../cpp/ellipses-and-variadic-templates.md)和省略号和默认自变量中[后缀表达式](../cpp/postfix-expressions.md)。  
  
 使用参数`...`必须是参数列表中的最后一个参数。  
  
## <a name="example"></a>示例  
  
### <a name="code"></a>代码  
  
```  
// mcppv2_paramarray.cpp  
// compile with: /clr  
using namespace System;  
double average( ... array<Int32>^ arr ) {  
   int i = arr->GetLength(0);  
   double answer = 0.0;  
  
   for (int j = 0 ; j < i ; j++)  
      answer += arr[j];  
  
   return answer / i;  
}  
  
int main() {  
   Console::WriteLine("{0}", average( 1, 2, 3, 6 ));  
}  
```  
  
### <a name="output"></a>输出  
  
```  
3  
```  
  
## <a name="code-example"></a>代码示例  
 下面的示例演示如何从 C# 调用采用数目可变的参数的 Visual c + + 函数。  
  
```  
// mcppv2_paramarray2.cpp  
// compile with: /clr:safe /LD  
using namespace System;  
  
public ref class C {  
public:   
   void f( ... array<String^>^ a ) {}  
};  
```  
  
 该函数`f`可以从调用 C# 或 Visual Basic 中，例如，像它是可以采用数量可变的自变量的函数。  
  
 在 C# 中，自变量传递给`ParamArray`参数可以由数目可变的参数。 下面的代码示例采用 C#。  
  
```  
// mcppv2_paramarray3.cs  
// compile with: /r:mcppv2_paramarray2.dll  
// a C# program  
  
public class X {  
   public static void Main() {  
      // Visual C# will generate a String array to match the   
      // ParamArray attribute  
      C myc = new C();  
      myc.f("hello", "there", "world");  
   }  
}  
```  
  
 调用`f`Visual c + + 中可以传递初始化的数组或可变长度数组。  
  
```  
// mcpp_paramarray4.cpp  
// compile with: /clr  
using namespace System;  
  
public ref class C {  
public:   
   void f( ... array<String^>^ a ) {}  
};  
  
int main() {  
   C ^ myc = gcnew C();  
   myc->f("hello", "world", "!!!");  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [数组](../windows/arrays-cpp-component-extensions.md)
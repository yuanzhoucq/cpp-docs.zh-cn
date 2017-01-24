---
title: "变量参数列表 (...) (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "参数数组"
  - "变量参数列表"
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 变量参数列表 (...) (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此示例演示了如何在 Visual C\+\+ 中使用 `...` 语法实现参数数目可变的功能。  
  
> [!NOTE]
>  本主题与 C\+\+\/CLI 相关。  有关使用 ISO 标准 C\+\+ 中 `...` 的信息，请参阅 [省略号和可变参数模板](../cpp/ellipses-and-variadic-templates.md) 和 [省略号和默认自变量](../misc/ellipses-and-default-arguments.md)。  
  
 使用 `...` 参数必须是参数列表中位于最后面的参数。  
  
## 示例  
  
### 代码  
  
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
  
### Output  
  
```  
3  
```  
  
## 代码示例  
 以下示例演示如何从 C\# 调用采用参数数目可变的 Visual C\+\+ 功能。  
  
```  
// mcppv2_paramarray2.cpp  
// compile with: /clr:safe /LD  
using namespace System;  
  
public ref class C {  
public:   
   void f( ... array<String^>^ a ) {}  
};  
```  
  
 例如，可以从 C\# 或 Visual Basic 调用函数 `f`，就好像它是一个可以采用可变数目参数的函数。  
  
 在 C\# 中，传递给 `ParamArray` 参数的参数可以由可变数量的参数调用。  以下代码示例在 C\# 中。  
  
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
  
 调用 Visual C\+\+ 中的 `f` 可以通过一个初始化数组或一个变长数组。  
  
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
  
## 请参阅  
 [数组](../windows/arrays-cpp-component-extensions.md)
---
title: "C 风格的强制转换和 /clr (C++/CLI) | Microsoft Docs"
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
  - "C 风格的强制转换和 /clr"
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C 风格的强制转换和 /clr (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以下主题仅适用于公共语言运行时。  
  
 在使用与 CLR 类型，编译器尝试映射转换为 C 样式的顺序列出的，其中的一种转换：  
  
1.  const\_cast  
  
2.  safe\_cast  
  
3.  safe\_cast 以及 const\_cast  
  
4.  static\_cast  
  
5.  static\_cast 以及 const\_cast  
  
 如果转换都没有有效，上面列出，因此，如果表达式的类型和对象类型都是 CLR 引用类型，C 样式为运行时检查 \(castclass MSIL 指令转换\) 的映射。  否则，C. 式转换考虑无效编译器问题和错误。  
  
## 备注  
 不建议用 C 式转换。  当用编译时，请使用 [\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)[safe\_cast](../windows/safe-cast-cpp-component-extensions.md)。  
  
 下面的示例演示映射到 C. `const_cast`的样式转换。  
  
```  
// cstyle_casts_1.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
int main() {  
   const R^ constrefR = gcnew R();  
   R^ nonconstR = (R^)(constrefR);   
}  
```  
  
 下面的示例演示映射到 C. `safe_cast`的样式转换。  
  
```  
// cstyle_casts_2.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   Object ^ o = "hello";  
   String ^ s = (String^)o;  
}  
```  
  
 下面的示例演示映射到 C. `safe_cast` plus `const_cast`的样式转换。  
  
```  
// cstyle_casts_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
ref struct R2 : public R {};  
  
int main() {  
   const R^ constR2 = gcnew R2();  
   try {  
   R2^ b2DR = (R2^)(constR2);  
   }  
   catch(InvalidCastException^ e) {  
      System::Console::WriteLine("Invalid Exception");  
   }  
}  
```  
  
 下面的示例演示映射到 C. `static_cast`的样式转换。  
  
```  
// cstyle_casts_4.cpp  
// compile with: /clr  
using namespace System;  
  
struct N1 {};  
struct N2 {  
   operator N1() {  
      return N1();  
   }  
};  
  
int main() {  
   N2 n2;  
   N1 n1 ;  
   n1 = (N1)n2;  
}  
```  
  
 下面的示例演示映射到 C. `static_cast` plus `const_cast`的样式转换。  
  
```  
// cstyle_casts_5.cpp  
// compile with: /clr  
using namespace System;  
struct N1 {};  
  
struct N2 {  
   operator const N1*() {  
      static const N1 n1;  
      return &n1;  
   }  
};  
  
int main() {  
   N2 n2;  
   N1* n1 = (N1*)(const N1*)n2;   // const_cast + static_cast  
}  
```  
  
 下面的示例演示映射到 C. 运行时检查的项转换。  
  
```  
// cstyle_casts_6.cpp  
// compile with: /clr  
using namespace System;  
  
ref class R1 {};  
ref class R2 {};  
  
int main() {  
   R1^ r  = gcnew R1();  
   try {  
      R2^ rr = ( R2^)(r);  
   }  
   catch(System::InvalidCastException^ e) {  
      Console::WriteLine("Caught expected exception");  
   }  
}  
```  
  
 下面的示例演示一种无效 C 样式转换，会导致编译器发出错误。  
  
```  
// cstyle_casts_7.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   String^s = S"hello";  
   int i = (int)s;   // C2440  
}  
```  
  
## 要求  
 编译器选项：**\/clr**  
  
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)
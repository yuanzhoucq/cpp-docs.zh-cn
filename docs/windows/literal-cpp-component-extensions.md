---
title: "文本 (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "literal"
  - "literal_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "文本关键字 [C++]"
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 文本 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

变量 \(数据成员\) 指示的，因为在 **\/clr** 编译中的 `literal` 是 `static const` 本机项变量。  
  
## 所有平台  
 **备注**  
  
 （无适用于所有运行时的语言功能的备注。）  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **备注**  
  
 \(此语言功能没有只适用于 Windows 运行时的备注。）  
  
### 要求  
 编译器选项：**\/ZW**  
  
## 公共语言运行时  
  
## 备注  
 在声明和值必须为常量整型、枚举或字符串类型，被标记为 `literal`的数据成员必须被初始化。  从初始化表达式类型的转换为的常量静态数据成员的类型不能需要用户定义的转换。  
  
 内存没有为运行时中的文本字段分配；编译器只将其在元数据中的类的值插入。  
  
 变量被标记的 `static const` 不是可用在元数据到其他编译器。  
  
 有关更多信息，请参见[Static](../misc/static-cpp.md)和[const](../cpp/const-cpp.md)。  
  
 `literal` 是上下文相关的关键字。  有关更多信息，请参见[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
## 示例  
 此示例演示，`literal` 变量表示 `static`。  
  
```  
// mcppv2_literal.cpp  
// compile with: /clr  
ref struct X {  
   literal int i = 4;  
};  
  
int main() {  
   int value = X::i;  
}  
```  
  
## 示例  
 下面的示例演示元数据显示文本影响：  
  
```  
// mcppv2_literal2.cpp  
// compile with: /clr /LD  
public ref struct A {  
   literal int lit = 0;  
   static const int sc = 1;  
};  
```  
  
 注意在元数据中的 `sc` 和 `lit`的差异：`modopt` 指令应用于 `sc`，这意味着它可能由其他编译器忽略。  
  
```  
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)  
```  
  
```  
.field public static literal int32 lit = int32(0x0000000A)  
```  
  
## 示例  
 下例，编写 C\#，引用上一示例中创建的元数据并显示 `literal` 和 `static const` 变量影响：  
  
```  
// mcppv2_literal3.cs  
// compile with: /reference:mcppv2_literal2.dll  
// A C# program  
class B {  
   public static void Main() {  
      // OK  
      System.Console.WriteLine(A.lit);  
      System.Console.WriteLine(A.sc);  
  
      // C# does not enforce C++ const  
      A.sc = 9;  
      System.Console.WriteLine(A.sc);  
  
      // C# enforces const for a literal  
      A.lit = 9;   // CS0131  
  
      // you can assign a C++ literal variable to a C# const variable  
      const int i = A.lit;  
      System.Console.WriteLine(i);  
  
      // but you cannot assign a C++ static const variable  
      // to a C# const variable  
      const int j = A.sc;   // CS0133  
      System.Console.WriteLine(j);  
   }  
}  
```  
  
## 要求  
 编译器选项：**\/clr**  
  
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)
---
title: "for each，in | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::foreach"
  - "for"
  - "each"
  - "in"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "for each 关键字 [C++]"
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# for each，in
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过数组或集合迭代。  此非标准关键字在 C\+\+\/CLI 和本机 C\+\+ 项目中可用。  但是，建议不使用它。  考虑改用标准 [基于范围的 for 语句 \(C\+\+\)](../cpp/range-based-for-statement-cpp.md)。  
  
## 所有运行时  
 **语法**  
  
```  
  
        for each (type identifier in expression) {  
   statements  
}  
  
```  
  
 **参数**  
  
 `type`  
 `identifier` 的类型。  
  
 `identifier`  
 代表集合元素的迭代变量。当 `identifier` 为[% \(跟踪引用\)](../windows/tracking-reference-operator-cpp-component-extensions.md)时，可以修改该元素。  
  
 `expression`  
 数组表达式或集合。  集合元素必须让编译器能将其转换为 `identifier` 类型。  
  
 `statements`  
 要执行的一个或多个语句。  
  
 **备注**  
  
 `for each` 语句用于循环访问集合。  可修改集合中的元素，但无法添加或删除元素。  
  
 对数组或集合中的每个元素执行 *statements*。  为集合中的所有元素完成迭代后，控制将传递给 `for each` 块之后的语句。  
  
 `for each` 和 `in` 是[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
 更多相关信息：  
  
-   [使用 for each 循环访问 STL 集合](../dotnet/iterating-over-stl-collection-by-using-for-each.md)  
  
-   [如何：使用 for each 循环访问数组](../dotnet/how-to-iterate-over-arrays-with-for-each.md)  
  
-   [如何：使用 for each 循环访问泛型集合](../dotnet/how-to-iterate-over-a-generic-collection-with-for-each.md)  
  
-   [如何：使用 for each 循环访问用户定义集合](../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md)  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
  
### 要求  
 编译器选项：**\/ZW**  
  
### 示例  
 本示例演示了如何使用 `for each` 来循环访问字符串。  
  
```  
// for_each_string1.cpp  
// compile with: /ZW  
#include <stdio.h>  
using namespace Platform;  
  
ref struct MyClass {  
   property String^ MyStringProperty;  
};  
  
int main() {  
   String^ MyString = ref new String("abcd");  
  
   for each ( char c in MyString )  
      wprintf("%c", c);  
  
   wprintf("/n");  
  
   MyClass^ x = ref new MyClass();  
   x->MyStringProperty = "Testing";  
  
   for each( char c in x->MyStringProperty )  
      wprintf("%c", c);  
}  
```  
  
 **输出**  
  
  **abcd**  
 **测试**   
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **备注**  
  
 CLR 语法与**所有运行时**语法相同，但有以下差异。  
  
 *expression*  
 托管的数组表达式或集合。  集合元素必须让编译器能将其从 <xref:System.Object> 转换为 *identifier* 类型。  
  
 *expression* 的计算结果为实现 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601> 的类型，或定义 `GetEnumerator` 方法（此方法可返回实现 <xref:System.Collections.IEnumerator> 的类型或声明 `IEnumerator` 中定义了所有方法）的类型。  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 本示例演示了如何使用 `for each` 来循环访问字符串。  
  
```  
// for_each_string2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct MyClass {  
   property String ^ MyStringProperty;  
};  
  
int main() {  
   String ^ MyString = gcnew String("abcd");  
  
   for each ( Char c in MyString )  
      Console::Write(c);  
  
   Console::WriteLine();  
  
   MyClass ^ x = gcnew MyClass();  
   x->MyStringProperty = "Testing";  
  
   for each( Char c in x->MyStringProperty )  
      Console::Write(c);  
}  
```  
  
 **输出**  
  
  **abcd**  
 **测试**   
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)
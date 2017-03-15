---
title: "字符串 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字符串"
  - "字符串 [C++], 字符串"
ms.assetid: 6d1fc3f8-0d58-4d68-9678-16b4f6dc4766
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 字符串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，字符串的处理已发生更改。  
  
 在 C\+\+ 托管扩展语言设计中，通过对字符串添加前缀 `S` 来表示托管字符串。  例如：  
  
```  
String *ps1 = "hello";  
String *ps2 = S"goodbye";  
```  
  
 两个初始化操作之间的性能系统开销并不是微不足道的，如以下 CIL 表示形式所演示的（也可以通过 **ildasm** 看到）：  
  
```  
// String *ps1 = "hello";  
ldsflda    valuetype $ArrayType$0xd61117dd  
     modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier)   
     '?A0xbdde7aca.unnamed-global-0'  
  
newobj instance void [mscorlib]System.String::.ctor(int8*)  
stloc.0  
  
// String *ps2 = S"goodbye";  
ldstr      "goodbye"  
stloc.0  
```  
  
 由于只需要记住（或了解）向字符串加前缀 `S`，所以这是一种非常省事的方法。  在新语法中，字符串的处理变得透明，并由使用的上下文确定。  不再需要指定 `S`。  
  
 在需要显式指示编译器采用一种或另一种解释的情况下会怎样呢？  在这些情况下，我们应用显式强制转换。  例如：  
  
```  
f( safe_cast<String^>("ABC") );  
```  
  
 此外，现在字符串使用简单转换（而不是标准转换）来匹配 `String`。  然而这可能与它更改重载函数集的解析不大相同，该函数集包括作为竞争形参的 `String` 和 `const char*`。  此解析以前被解析为 `const char*` 实例，现在被标记为不明确。  例如：  
  
```  
ref struct R {  
   void f(const char*);  
   void f(String^);  
};  
  
int main () {  
   R r;  
   // old syntax: f( const char* );  
   // new syntax: error: ambiguous  
   r.f("ABC");   
}  
```  
  
 为什么存在差异？  由于程序内存在多个名为 `f` 的实例，这就需要将函数重载解析算法应用于调用。  重载函数的形式解析涉及三个步骤。  
  
1.  候选函数的集合。  候选函数是范围内与被调用函数的名称在词法上匹配的那些方法。  例如，由于 `f()` 是通过 `R` 的实例调用的，非 `R`（或其基类层次结构）的成员的所有命名函数 `f` 都不是候选函数。  此示例中存在两个候选函数。  它们是名为 `f` 的 `R` 的两个成员函数。  如果该候选函数集为空，则此阶段中的调用将失败。  
  
2.  来自候选函数的可行函数集。  可行函数是在给定参数数量及其类型的条件下可使用调用中指定的参数来调用的函数。  在本示例中，两个候选函数也都是可行函数。  如果可行函数集为空，则此阶段中的调用将失败。  
  
3.  选择表示与调用最佳匹配的函数。  这是通过以下操作实现的：对应用的转换进行分级，将变量转换为可行函数参数的类型。  对于单参数函数，这是相对简单的；当存在多个参数时，会变得稍微复杂些。  如果不存在最佳匹配，此阶段中的调用将失败。  也就是说，如果需要将实参类型转换为形参类型的转换，也是同样可行的。  将该调用标记为不明确。  
  
 在托管扩展中，此调用的解析调用作为最佳匹配的 `const char*` 实例。  在新语法中，将 `"abc"` 与 `const char*` 和与 `String^` 进行匹配所需的转换现在是等效的（即同样好的），因此将此调用标记为坏的（即不明确的）。  
  
 这将导致两个问题：  
  
-   实参 `"abc"` 的类型是什么？  
  
-   用于确定哪种类型转换更好的算法是什么？  
  
 字符串 `"abc"` 的类型为 `const char[4]` — 请记住，在每个字符串的末尾都有一个隐式的 null 终止字符。  
  
 用于确定哪种类型转换更好的算法涉及在层次结构中查找可能的类型转换。  这是我对该层次结构的理解 — 当然，所有这些转换都是隐式的。  使用显式强制转换表示法重写层次结构类似于使用括号重写表达式的常用运算符优先级。  
  
1.  精确匹配是最佳的。  令人惊讶的是，要使参数成为精确匹配，不需要完全匹配参数类型；只需足够接近就可以了。  这是理解此示例中的内容和语言如何更改的关键。  
  
2.  提升优于标准转换。  例如，将 `short int` 提升为 `int` 好于将 `int` 转换为 `double`。  
  
3.  标准转换优于装箱转换。  例如，将 `int` 转换为 `double` 好于将 `int` 装箱到 `Object`。  
  
4.  装箱转换优于隐式的用户定义转换。  例如，将 `int` 装箱到 `Object` 好于应用 `SmallInt` 值类的转换运算符。  
  
5.  隐式的用户定义转换优于根本不进行任何转换。  隐式的用户定义转换是发生错误（同时发出警告：形式签名在该位置可能包含参数数组或省略号）之前的最后的出口。  
  
 因此，如果说精确匹配在完全意义上不必是一个匹配，那意味着什么？  例如，`const char[4]` 与 `const char*` 和 `String^` 并不完全匹配，但此示例的不明确性就出现在两个冲突的精确匹配之间！  
  
 在出现精确匹配时，它包含多种常用转换。  ISO\-C\+\+ 中存在四种可应用的常用转换，它们仍作为精确匹配。  其中三种称为左值转换。  第四种类型称为限定转换。  这三种左值转换被视为比要求限定转换的匹配更佳的精确匹配。  
  
 一种形式的左值转换是“本机数组到指针”转换。  将 `const char[4]` 与 `const char*` 匹配所涉及的转换便为此种形式的转换。  因此，`f("abc")` 与 `f(const char*)` 的匹配是精确匹配。  事实上，在以前的语言版本中，这是最佳匹配。  
  
 因此，要使编译器将调用标记为不明确，要求 `const char[4]` 到 `String^` 的转换也是通过常用转换进行的精确匹配。  这是已在新语言版本中引入的更改。  这也是现在将调用标记为不明确的原因。  
  
## 请参阅  
 [常规语言更改](../dotnet/general-language-changes-cpp-cli.md)   
 [String](../windows/string-cpp-component-extensions.md)
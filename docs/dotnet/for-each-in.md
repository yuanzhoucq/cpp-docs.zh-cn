---
title: 对于每个，在 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::foreach
- for
- each
- in
dev_langs:
- C++
helpviewer_keywords:
- for each keyword [C++]
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a55425c891999142fe32ae08125cce22728daffa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040683"
---
# <a name="for-each-in"></a>for each, in
通过数组或集合迭代。 此非标准关键字在 C++/CLI 和本机 C++ 项目中可用。 但是，建议不使用它。 请考虑使用标准[基于范围的 for 语句 （c + +）](../cpp/range-based-for-statement-cpp.md)相反。  
  
## <a name="all-runtimes"></a>所有运行时  
 **语法**  
  
```  
  
      for each (typeidentifierinexpression) {  
   statements  
}  
  
```  
  
 **参数**  
  
*type*<br/>
`identifier` 的类型。  
  
*identifier*<br/>
代表集合元素的迭代变量。  当`identifier`是[跟踪引用运算符](../windows/tracking-reference-operator-cpp-component-extensions.md)，可以修改该元素。  
  
*表达式*<br/>
数组表达式或集合。 集合元素必须让编译器能将其转换为 `identifier` 类型。  
  
*语句*<br/>
要执行的一个或多个语句。  
  
 **备注**  
  
 `for each` 语句用于循环访问集合。 可修改集合中的元素，但无法添加或删除元素。  
  
 *语句*数组或集合中每个元素执行。 为集合中的所有元素完成迭代后，控制将传递给 `for each` 块之后的语句。  
  
 `for each` 并`in`都[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
 更多相关信息：  
  
-   [使用 for each 循环访问 C++ 标准库集合](../dotnet/iterating-over-stl-collection-by-using-for-each.md)  
  
-   [如何：使用 for each 循环访问数组](../dotnet/how-to-iterate-over-arrays-with-for-each.md)  
  
-   [如何：使用 for each 循环访问泛型集合](../dotnet/how-to-iterate-over-a-generic-collection-with-for-each.md)  
  
-   [如何：使用 for each 循环访问用户定义集合](../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md)  
  
## <a name="windows-runtime"></a>Windows 运行时  
  
### <a name="requirements"></a>要求  
 编译器选项： **/ZW**  
  
### <a name="example"></a>示例  
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
  
```Output  
abcd  
  
Testing  
```  
  
## <a name="common-language-runtime"></a>公共语言运行时 
 **备注**  
  
 CLR 语法等同于**所有运行时**语法中，按如下所示除外。  
  
 *表达式*  
 托管的数组表达式或集合。 集合元素必须让编译器可以将其从转换<xref:System.Object>到*标识符*类型。  
  
 *表达式*计算结果为的类型实现<xref:System.Collections.IEnumerable>， <xref:System.Collections.Generic.IEnumerable%601>，或定义的类型`GetEnumerator`方法可返回一种类型的实现<xref:System.Collections.IEnumerator>声明所有中定义的方法或`IEnumerator`.  
  
### <a name="requirements"></a>要求  
 编译器选项： **/clr**  
  
### <a name="example"></a>示例  
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
  
```Output  
abcd  
  
Testing   
```  
  
## <a name="see-also"></a>请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)
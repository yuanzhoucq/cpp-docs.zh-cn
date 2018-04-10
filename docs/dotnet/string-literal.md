---
title: 字符串文本 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- string literals
- strings [C++], string literals
ms.assetid: 6d1fc3f8-0d58-4d68-9678-16b4f6dc4766
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dd62f85b87473d1371daf2d2fa009d8620e59b57
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="string-literal"></a>字符串
字符串文本处理已从托管扩展中的 c + + 更改为 Visual c + +。  
  
 在 c + + 语言设计托管扩展中，托管的字符串文本已由对字符串添加前缀与指示`S`。 例如:  
  
```  
String *ps1 = "hello";  
String *ps2 = S"goodbye";  
```  
  
 两个初始化操作开销之间的性能结果，非普通，如以下 CIL 表示形式所演示所示**ildasm**:  
  
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
  
 这与可用于只需记住 （或学习） 是文字字符串的前缀显著节省`S`。 在新语法中，字符串文本的处理进行透明的由使用的上下文。 `S`不再需要指定。  
  
 情况下在其中我们需要显式直接与一个解释或另一个编译器？ 在这些情况下，我们将应用的显式转换。 例如:  
  
```  
f( safe_cast<String^>("ABC") );  
```  
  
 此外，字符串文本现在匹配`String`使用简单的转换，而不是标准转换。 虽然这不可能看起来像得多更改的重载的函数集包括分辨率`String`和`const char*`作为竞争的正式参数。 一次解析为的分辨率`const char*`实例现在已标记为不明确。 例如:  
  
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
  
 原因有什么区别？ 由于多个名为实例`f`存在在程序内，这要求要应用于调用的函数重载解析算法。 重载函数的形式解析涉及三个步骤。  
  
1.  候选函数的集合。 候选函数是函数的作用域内词法与要调用名称相匹配的那些方法。 例如，由于`f()`的实例通过调用`R`，所有名为函数`f`不属于`R`（或其基的类层次结构的指针） 都不是候选函数。 在本示例中，有两个候选函数。 这些是两个成员函数的`R`名为`f`。 候选函数集是否为空，则此阶段中调用将失败。  
  
2.  候选函数从可行函数集。 可行函数是可以使用调用过程中，指定给定自变量和参数类型的数量的参数调用。 在本示例中，这两个候选函数也是可行的函数。 如果可行函数集为空，则此阶段中调用将失败。  
  
3.  选择表示最佳匹配调用的函数。 这是通过排名用于转换的可行函数参数的类型的自变量的转换。 这是比较直接的操作使用单个参数函数;如果有多个参数，它将成为某种程度上更复杂。 如果没有最佳匹配项，则此阶段中调用将失败。 也就是说，如果转换的类型形参的实际自变量的类型所需的转换是很好。 将该调用标记为不明确。  
  
 在托管扩展中，调用此调用的分辨率`const char*`作为最佳匹配项的实例。 在新的语法中，匹配所需转换`"abc"`到`const char*`和`String^`现，它是等效的很好的因此调用标记为不正常的即为不明确。  
  
 这将导致两个问题：  
  
-   实际自变量类型是什么`"abc"`？  
  
-   用于确定当一个类型转换为另一个更好的算法是什么？  
  
 字符串文本类型`"abc"`是`const char[4]`-请记住，文本是一个隐式的 null 终止字符，在每个字符串的末尾。  
  
 用于确定当一个类型转换为另一个更好的算法涉及层次结构中放置的可能类型转换。 下面是我了解该层次结构-所有这些，当然，为隐式转换。 使用显式强制转换表示法重写层次结构相似的方式括号替代表达式的常用运算符优先级。  
  
1.  完全匹配是最佳的。 因此，要成为精确匹配参数，它不需要精确匹配的参数类型;它只需是近到足以。 这是了解当前进行的操作在此示例中，和更改语言的方式中的密钥。  
  
2.  促销优于标准转换。 例如，将提升`short int`到`int`优于转换`int`到`double`。  
  
3.  标准转换优于装箱转换。 例如，转换`int`到`double`是更好地装箱`int`到`Object`。  
  
4.  装箱转换优于隐式的用户定义的转换。 例如，装箱`int`到`Object`优于应用转换运算符的`SmallInt`值类。  
  
5.  隐式的用户定义的转换不优于任何转换根本。 隐式的用户定义的转换是最后一个退出之前错误 （具有需要注意的正式签名可能包含的参数数组或该位置处的省略号）。  
  
 因此，它意味着什么说完全匹配，不一定完全匹配？ 例如，`const char[4]`不完全匹配以下其中一个`const char*`或`String^`，还有我们的示例中的不确定性是之间两个冲突的精确匹配 ！  
  
 完全匹配，事件发生，包括常用转换的数字。 有四个常用转换下 ISO c + +，可以应用仍才会被视为完全匹配。 三个统称为左值转换。 第四种类型称为限定转换。 三个左值转换将被视为比要求限定转换更好地完全匹配。  
  
 一种形式的左值转换为本机指针数组的转换。 这是在匹配中所涉及的内容`const char[4]`到`const char*`。 因此的匹配项`f("abc")`到`f(const char*)`是完全匹配。 在以前的我们，这是语言的最佳匹配中的事实。  
  
 编译器将调用标记为不明确的因此，所需要的转换`const char[4]`到`String^`也是通过普通转换完全匹配。 这是新的语言版本中引入了更改。 这就是为什么调用现在已标记为不明确。  
  
## <a name="see-also"></a>请参阅  
 [常规语言更改 (C + + /cli CLI)](../dotnet/general-language-changes-cpp-cli.md)   
 [字符串](../windows/string-cpp-component-extensions.md)
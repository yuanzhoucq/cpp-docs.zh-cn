---
title: 字符串文本 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- string literals
- strings [C++], string literals
ms.assetid: 6d1fc3f8-0d58-4d68-9678-16b4f6dc4766
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 41f1996cd4f4caf24ac08d09b05e636cb09f7eed
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415260"
---
# <a name="string-literal"></a>字符串

字符串文本的处理已从托管扩展中的 c + + 更改为 Visual c + +。

在 c + + 语言设计托管扩展中，通过字符串添加前缀表示托管的字符串`S`。 例如：

```
String *ps1 = "hello";
String *ps2 = S"goodbye";
```

两个初始化操作开销之间的性能结果，重要的如以下 CIL 表示形式所演示所示**ildasm**:

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

这是省事的只是记住 （或学习） 前缀的文本字符串与`S`。 在新语法中，字符串文本的处理进行透明的由使用的上下文。 `S`不再需要指定。

怎样情况下在其中我们需要显式定向到一个解释或其他编译器？ 在这些情况下，我们将应用显式强制转换。 例如：

```
f( safe_cast<String^>("ABC") );
```

此外，字符串文本现在匹配`String`与简单的转换而不是标准转换。 这不可能看起来像在更改的重载的函数集，其中包括分辨率更`String`和一个`const char*`作为竞争的正式参数。 一次被解析为的分辨率`const char*`实例现在已标记为不明确。 例如：

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

为什么有什么区别？ 由于多个名为实例`f`存在在程序中，这要求要应用于调用的函数重载解析算法。 重载函数的形式解析涉及三个步骤。

1. 候选函数的集合。 候选函数都是函数的从词法上与要调用的名称相匹配的这些方法的作用域内。 例如，由于`f()`的实例通过调用`R`，则所有名为函数`f`的成员不是`R`（或其基的类层次结构的指针） 都不是候选函数。 在本示例中，有两个候选函数。 这些是的两个成员函数`R`名为`f`。 候选函数集是否为空，则此阶段中调用将失败。

1. 从候选函数的可行函数集。 可行函数是一个可调用使用指定的调用中给定数量的参数和它们的类型参数。 在本例中为这两个候选函数也是可行的函数。 如果可行函数集为空，则此阶段中调用将失败。

1. 选择表示最匹配的调用的函数。 这是排名应用转换为可行函数参数的类型参数的转换。 这是相对简单直接的单个参数函数;如果有多个参数，它变得有些复杂。 如果没有最佳匹配项，则此阶段中调用将失败。 也就是说，如果转换为类型形参的实参的类型所需的转换也是同样可行。 该调用会被标记为不明确。

在托管扩展中，调用此调用的分辨率`const char*`的最佳匹配的实例。 在新的语法中，匹配所需的转换`"abc"`到`const char*`和`String^`，它是现在是等效的很好的因此在调用标记为不正常状态的即为不明确。

这将导致两个问题：

- 自变量的类型是什么`"abc"`？

- 用于确定哪种类型转换比另一个更好的算法是什么？

字符串文字的类型`"abc"`是`const char[4]`-请记住，文本是隐式 null 终止的字符的每个字符串的末尾。

用于确定哪种类型转换优于另一种算法涉及到在层次结构中放置的可能类型转换。 下面是我了解该层次结构-所有这些转换，当然，是隐式的。 使用显式强制转换表示法将重写的方式类似的层次结构括号替代表达式的常用运算符优先级。

1. 是完全匹配。 因此，要完全匹配的参数，它不需要完全匹配的参数类型;它只需是足够接近。 这是了解这怎么回事在此示例中，以及如何更改语言具有密钥。

1. 促销优于标准转换。 例如，提升`short int`到`int`优于转换`int`到`double`。

1. 标准转换优于装箱转换。 例如，转换`int`成`double`是更好地装箱`int`到`Object`。

1. 装箱转换优于用户定义的隐式转换。 例如，装箱`int`成`Object`优于应用的转换运算符`SmallInt`值类。

1. 用户定义的隐式转换是根本比不进行转换。 用户定义的隐式转换为错误之前的最后一个 exit （具有需要注意的正式签名可能包含的参数数组或该位置处的省略号）。

因此，它意味着什么要说的完全匹配项，并不一定完全一样的匹配项？ 例如，`const char[4]`不完全匹配任一`const char*`或`String^`，还有我们的示例中的不确定性是两个冲突的精确匹配之间 ！

此时，完全匹配，包括常用转换的数字。 有四个常用转换在 ISO-C + + 可以应用，仍有资格作为完全匹配。 三个统称为左值的转换。 第四种类型称为限定转换。 三个左值转换被视为比要求限定转换更好地完全匹配。

一种形式的左值转换为本机指针数组的转换。 这是所涉及的匹配`const char[4]`到`const char*`。 因此的匹配项`f("abc")`到`f(const char*)`是完全匹配。 在以前的我们，这是语言的最佳匹配项，事实上。

编译器将调用标记为不明确的因此，所需要的转换`const char[4]`到`String^`也是通过不重要的转换完全匹配。 这是新的语言版本中引入了更改。 并且，这就是原因调用现在已标记为不明确。

## <a name="see-also"></a>请参阅

[常规语言更改 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
[字符串](../windows/string-cpp-component-extensions.md)
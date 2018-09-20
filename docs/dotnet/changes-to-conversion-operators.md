---
title: 将更改为转换运算符 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- conversion operators
- operators [C++], explicit type conversion
- type conversion, explicit conversions
- conversions, explicit
- explicit keyword [C++]
ms.assetid: 9b83925c-71b7-4bd3-ac2e-843dd7c7f184
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 03b17c5abc559289a9f85a10b9c5914b49498922
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381098"
---
# <a name="changes-to-conversion-operators"></a>转换运算符的更改

转换运算符的语法已从托管扩展中的 c + + 更改为 Visual c + +。

一个示例是编写`op_Implicit`来指定转换。 下面是定义`MyDouble`来自语言规范：

```
__gc struct MyDouble {
   static MyDouble* op_Implicit( int i );
   static int op_Explicit( MyDouble* val );
   static String* op_Explicit( MyDouble* val );
};
```

这意味着，给定一个整数，用于转换该整数算法`MyDouble`提供的`op_Implicit`运算符。 此外，该转换将隐式执行由编译器。 同样，给定`MyDouble`对象，这两个`op_Explicit`运算符将该对象转换成整数或托管提供各自的算法`String`实体。 但是，编译器将不执行此转换，除非用户显式请求。

在 C# 中，这种情况，如下所示：

```
class MyDouble {
   public static implicit operator MyDouble( int i );
   public static explicit operator int( MyDouble val );
   public static explicit operator string( MyDouble val );
};
```

C# 代码看起来更像 c + + 比用于 c + + 托管扩展。 不是这种情况在新语法。

ISO c + + 委员会引入了新关键字`explicit`，以减少意外的结果-例如，`Array`类它采用一个整型参数，如维度会隐式转换到的任何整数`Array`对象的是不是你想要。 若要防止这种情况的一种方法是虚拟的第二个参数构造函数的一个设计惯例

但是，设计 c + + 中的类类型时，不应提供一个转换对。 最好的例子是标准字符串类。 隐式转换为 C 样式字符串的单自变量构造函数。 但是，它不提供相应的隐式转换运算符的将字符串转换的对象复制到 C 样式字符串，而又而不是要求用户显式调用命名的函数-在这种情况下， `c_str()`。

因此，将关联的转换运算符 （以及作为封装到一个窗体的声明转换的集合） 的隐式/显式行为似乎是转换运算符，这最终导致原始c++支持的改进`explicit`关键字。 转换运算符的 Visual c + + 语言支持如下所示，这是比 C# 的详细程度略低由于运算符支持的转换算法的隐式应用程序的默认行为：

```
ref struct MyDouble {
public:
   static operator MyDouble^ ( int i );
   static explicit operator int ( MyDouble^ val );
   static explicit operator String^ ( MyDouble^ val );
};
```

另一项更改是一个自变量构造函数被视为如同它被声明为`explicit`。 这意味着，若要触发它的调用，显式强制转换，则需要。 但是，请注意，是否定义的显式转换运算符，它并不单自变量构造函数，调用。

## <a name="see-also"></a>请参阅

[类或接口中的成员声明 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)
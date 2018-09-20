---
title: 参数数组和省略号 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- function overloading, argument matching
ms.assetid: 492e3f6c-1c4c-4e0c-a358-72f2d39c30be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2caf6415fdbceb506b736e209c6e7e384b567c5a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384372"
---
# <a name="param-array-and-ellipsis"></a>参数数组和省略号

参数数组用于解析重载的函数调用的优先级已从托管扩展中的 c + + 更改为 Visual c + +。

在托管扩展和新语法中，是对 C# 和 Visual Basic 支持的参数数组不显式支持。 相反，标记所示的特性，普通的数组，如下所示：

```
void Trace1( String* format, [ParamArray]Object* args[] );
void Trace2( String* format, Object* args[] );
```

虽然这两项都看起来相同，`ParamArray`特性将此标记的 C# 或其他 CLR 语言作为元素每次调用具有可变数量的数组。 解析重载函数中的一个实例声明一个省略号设置中为托管扩展和新语法之间的程序中的行为更改，第二个声明`ParamArray`属性，如以下示例提供的Artur Laksberg。

```
int fx(...); // 1
int fx( [ParamArray] Int32[] ); // 2
```

在托管扩展中，省略号的优先级高于这是合理的因为该属性不是一个正式的语言方面的属性。 但是，在新语法中，参数数组现在支持直接在语言中，因为它更强类型的省略号上提供优先顺序。 因此，在托管扩展中，调用

```
fx( 1, 2 );
```

解析为`fx(...)`中的新语法，它解析为`ParamArray`实例。 在您程序的行为取决于省略号实例的调用而不关闭机会`ParamArray`，将需要修改签名或调用。

## <a name="see-also"></a>请参阅

[常规语言更改 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)
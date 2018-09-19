---
title: 解决不明确声明 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 3d773ee7-bbea-47de-80c2-cb0a9d4ec0b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1e55d5afc3cc95dbfd61bead30cdb2d686f7f30
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066631"
---
# <a name="resolving-ambiguous-declarations-c"></a>解决不明确声明 （C++）

若要执行从一种类型到另一种类型的显式转换，您必须使用强制转换并指定所需的类型名称。 某些类型转换会导致句法歧义。 下面的函数样式类型转换是不明确的：

```cpp
char *aName( String( s ) );
```

不清楚是否函数声明或使用函数样式转换作为初始值设定项的对象声明： 它可以声明返回类型的函数`char *`采用一个自变量类型的`String`，也可以声明的对象`aName`并将其初始化的值与`s`强制转换为类型`String`。

如果声明可被视为有效的函数声明，则会以相同的方式处理。 只有当它不能是函数声明时（即句法不正确时），才会查看语句是否为函数样式类型转换。 因此，编译器将语句视为函数的声明并忽略标识符 `s` 周围的括号。 另一方面，语句：

```cpp
char *aName( (String)s );
```

和

```cpp
char *aName = String( s );
```

显然是声明的对象和类型的用户定义的转换`String`键入`char *`调用来执行的初始化`aName`。
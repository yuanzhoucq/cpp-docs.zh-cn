---
title: 编译器警告（等级 1）C4788
ms.date: 11/04/2016
f1_keywords:
- C4788
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
ms.openlocfilehash: c51a4409c2a3028823462539343654b5eac365d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598167"
---
# <a name="compiler-warning-level-1-c4788"></a>编译器警告（等级 1）C4788

identifier： 标识符被截断为 number 个字符

编译器限制的函数名称允许的最大长度。 当编译器生成 funclets EH/SEH 代码时，它形成 funclet 名称通过预先计算函数名称加上一些文本，例如"__catch"，"\__unwind"，或另一个字符串。

生成的 funclet 名称可能太长，并且编译器将其截断，并生成 C4788。

若要解决此警告，请缩短原始函数名称。 如果函数是 c + + 模板函数或方法，使用 typedef 名称的一部分。 例如：

```
C1<x, y, z<T>>::C2<a,b,c>::f
```

可以替换为：

```
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;
new_class::f
```

此警告仅发生在 x64 编译器。
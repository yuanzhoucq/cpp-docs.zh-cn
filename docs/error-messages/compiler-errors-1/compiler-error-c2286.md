---
title: 编译器错误 C2286
ms.date: 11/04/2016
f1_keywords:
- C2286
helpviewer_keywords:
- C2286
ms.assetid: 078e0201-35cc-42e2-8dbc-6f8cf557b098
ms.openlocfilehash: 79697a17d322ae15a21e522efa7dfd5c2342f7a6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759160"
---
# <a name="compiler-error-c2286"></a>编译器错误 C2286

指向 "identifier" 表示形式成员的指针已设置为 "继承"-声明已忽略

类存在两个不同的指向成员的指针表示形式。

有关详细信息，请参阅[继承关键字](../../cpp/inheritance-keywords.md)。

## <a name="example"></a>示例

下面的示例生成 C2286：

```cpp
// C2286.cpp
// compile with: /c
class __single_inheritance X;
class __multiple_inheritance X;   // C2286
class  __multiple_inheritance Y;   // OK
```

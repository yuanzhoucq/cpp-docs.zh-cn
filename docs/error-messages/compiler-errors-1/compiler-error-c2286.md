---
title: 编译器错误 C2286
ms.date: 11/04/2016
f1_keywords:
- C2286
helpviewer_keywords:
- C2286
ms.assetid: 078e0201-35cc-42e2-8dbc-6f8cf557b098
ms.openlocfilehash: 7d3b8297c5f5da29b99abe78999396e8c44df0fd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667501"
---
# <a name="compiler-error-c2286"></a>编译器错误 C2286

指向成员的 identifier 表示形式已设置为继承-忽略声明

类存在两个不同的指针到成员表示形式。

有关详细信息，请参阅[继承关键字](../../cpp/inheritance-keywords.md)。

## <a name="example"></a>示例

下面的示例生成 C2286：

```
// C2286.cpp
// compile with: /c
class __single_inheritance X;
class __multiple_inheritance X;   // C2286
class  __multiple_inheritance Y;   // OK
```
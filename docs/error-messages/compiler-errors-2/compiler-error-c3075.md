---
title: 编译器错误 C3075
ms.date: 11/04/2016
f1_keywords:
- C3075
helpviewer_keywords:
- C3075
ms.assetid: f431daa9-e0fa-48f0-a5c3-f99be96b55e3
ms.openlocfilehash: 345cdd17b9da0be8f8d6e9f7b5f48624ade412bd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761577"
---
# <a name="compiler-error-c3075"></a>编译器错误 C3075

“instance”：无法将引用类型“type”的实例嵌入到值类型中

值类型不能包含引用类型的实例。

有关详细信息，请参阅[ C++引用类型的堆栈语义](../../dotnet/cpp-stack-semantics-for-reference-types.md)。

## <a name="example"></a>示例

以下示例生成 C3075。

```cpp
// C3075.cpp
// compile with: /clr /c
ref struct U {};
value struct X {
   U y;   // C3075
};

ref struct Y {
   U y;   // OK
};
```

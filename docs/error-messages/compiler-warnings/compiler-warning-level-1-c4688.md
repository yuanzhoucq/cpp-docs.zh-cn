---
title: 编译器警告（等级 1）C4688
ms.date: 11/04/2016
f1_keywords:
- C4688
helpviewer_keywords:
- C4688
ms.assetid: a027df3c-b2b8-4c49-8539-c2bc42db74e8
ms.openlocfilehash: e7aebfa3ae602aa45c02897711cd94520a876cca
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175397"
---
# <a name="compiler-warning-level-1-c4688"></a>编译器警告（等级 1）C4688

“constraint”：约束列表包含程序集私有类型“type”

约束列表中有程序集私有类型，这意味着从程序集外部访问类型时，它将不可用。 有关详细信息，请参阅[泛型](../../extensions/generics-cpp-component-extensions.md)。

## <a name="example"></a>示例

以下示例生成 C4688。

```cpp
// C4688.cpp
// compile with: /clr /c /W1
ref struct A {};   // private type
public ref struct B {};

// Delete the following 3 lines to resolve.
generic <class T>
where T : A   // C4688
public ref struct M {};

generic <class T>
where T : B
public ref struct N {};
```

---
title: 编译器错误 C3399
ms.date: 11/04/2016
f1_keywords:
- C3399
helpviewer_keywords:
- C3399
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
ms.openlocfilehash: d20b5e816930969278536fe3771df4ad38c3c86b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737512"
---
# <a name="compiler-error-c3399"></a>编译器错误 C3399

“type”：创建泛型参数的实例时无法提供变量

当指定 `gcnew()` 约束时，指定约束类型将具有无参数的构造函数。 因此，尝试实例化此类型并传递参数是错误的。

有关详细信息，请参阅[泛型C++类型参数（/Cli）的约束](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)。

## <a name="example"></a>示例

以下示例生成 C3399。

```cpp
// C3399.cpp
// compile with: /clr /c
generic <class T>
where T : gcnew()
void f() {
   T t = gcnew T(1);   // C3399
   T t2 = gcnew T();   // OK
}
```

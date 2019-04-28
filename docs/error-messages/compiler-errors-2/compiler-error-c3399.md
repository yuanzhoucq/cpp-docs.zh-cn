---
title: 编译器错误 C3399
ms.date: 11/04/2016
f1_keywords:
- C3399
helpviewer_keywords:
- C3399
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
ms.openlocfilehash: d05a861a2baedb86482503b6860098f12c41bd78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300422"
---
# <a name="compiler-error-c3399"></a>编译器错误 C3399

“type”：创建泛型参数的实例时无法提供变量

当指定 `gcnew()` 约束时，指定约束类型将具有无参数的构造函数。 因此，尝试实例化此类型并传递参数是错误的。

请参阅[泛型类型参数的约束 (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)有关详细信息。

## <a name="example"></a>示例

以下示例生成 C3399。

```
// C3399.cpp
// compile with: /clr /c
generic <class T>
where T : gcnew()
void f() {
   T t = gcnew T(1);   // C3399
   T t2 = gcnew T();   // OK
}
```
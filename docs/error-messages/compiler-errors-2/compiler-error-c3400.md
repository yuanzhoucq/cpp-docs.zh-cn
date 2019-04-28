---
title: 编译器错误 C3400
ms.date: 11/04/2016
f1_keywords:
- C3400
helpviewer_keywords:
- C3400
ms.assetid: d44169a8-73b6-4766-b406-b3a6c93f2a4d
ms.openlocfilehash: c4b4cb64da83115ab5b6a5234cda2ea3c7ba3a53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300370"
---
# <a name="compiler-error-c3400"></a>编译器错误 C3400

涉及“constraint_1”和“constraint_2”的循环约束依赖项

编译器检测到循环约束。

有关详细信息，请参阅[泛型类型参数的约束 (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)。

## <a name="example"></a>示例

以下示例生成 C3400。

```
// C3400.cpp
// compile with: /clr /c
generic<class T, class U>
where T : U
where U : T   // C3400
public ref struct R {};
```
---
title: 编译器错误 C3218
ms.date: 11/04/2016
f1_keywords:
- C3218
helpviewer_keywords:
- C3218
ms.assetid: 0eea19e0-503e-4e07-ae8b-2cb2e95922cd
ms.openlocfilehash: 87084f9751b1593ec93a3062f23714bba403da9a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182517"
---
# <a name="compiler-error-c3218"></a>编译器错误 C3218

type： 不允许作为约束的类型

对于要约束的类型，它必须是值类型或对托管的类或接口的引用。

## <a name="example"></a>示例

下面的示例生成 C3218。

```
// C3218.cpp
// compile with: /clr /c
class A {};
ref class B {};

// Delete the following 3 lines to resolve.
generic <class T>
where T : A   // C3218
ref class C {};

// OK
generic <class T>
where  T : B
ref class D {};
```
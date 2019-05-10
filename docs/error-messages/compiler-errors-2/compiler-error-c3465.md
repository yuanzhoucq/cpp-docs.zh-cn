---
title: 编译器错误 C3465
ms.date: 11/04/2016
f1_keywords:
- C3465
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
ms.openlocfilehash: 117c9b9918950fd2e95e206c5aea457dee183b0a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222314"
---
# <a name="compiler-error-c3465"></a>编译器错误 C3465

若要使用类型“type”，必须引用程序集“assembly”

在重新编译客户端之前，类型转发都将适用于客户端应用程序。 重新编译时，包含客户端应用程序中所用类型定义的每个程序集都将需要一个引用。

有关详细信息，请参阅[类型转发 (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md)。

## <a name="example"></a>示例

以下示例生成包含类型新位置的程序集。

```
// C3465.cpp
// compile with: /clr /LD
public ref class R {
public:
   ref class N {};
};
```

## <a name="example"></a>示例

以下示例生成用来包含类型定义的程序集，但现在却包含此类型的转发语法。

```
// C3465_b.cpp
// compile with: /clr /LD
#using "C3465.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

## <a name="example"></a>示例

下面的示例生成 C3465。

```
// C3465_c.cpp
// compile with: /clr
// C3465 expected
#using "C3465_b.dll"
// Uncomment the following line to resolve.
// #using "C3465.dll"

int main() {
   R^ r = gcnew R();
}
```
---
title: 编译器错误 C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: 1dc9781bc0cf1bc6c7f879cc3971828983471c6f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757743"
---
# <a name="compiler-error-c2071"></a>编译器错误 C2071

"identifier"：非法的存储类

使用无效的[存储类](../../c-language/c-storage-classes.md)声明了 `identifier`。 为标识符指定多个存储类时或定义与存储类声明不兼容时，会导致此错误。

若要解决此问题，请了解标识符的预期存储类（例如 `static` 或 `extern`），并更正要匹配的声明。

## <a name="example"></a>示例

以下示例生成 C2071。

```cpp
// C2071.cpp
// compile with: /c
struct C {
   extern int i;   // C2071
};
struct D {
   int i;   // OK, no extern on an automatic
};
```

## <a name="example"></a>示例

以下示例生成 C2071。

```cpp
// C2071_b.cpp
// compile with: /c
typedef int x(int i) { return i; }   // C2071
typedef int (x)(int);   // OK, no local definition in typedef
```

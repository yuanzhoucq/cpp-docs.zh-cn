---
title: 编译器警告（等级 3）C4290
ms.date: 11/04/2016
f1_keywords:
- C4290
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
ms.openlocfilehash: c585294686298a1197d437d41a0d541f1268985f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402081"
---
# <a name="compiler-warning-level-3-c4290"></a>编译器警告（等级 3）C4290

C++忽略但指示函数的异常规范不是 __declspec （nothrow）

使用异常规范的视觉对象声明的函数C++接受，但未实现。 使用异常规范，将忽略在编译期间可能需要重新编译的代码和链接要重复使用在将来支持异常规范的版本。

有关详细信息，请参阅[异常规范 (throw)](../../cpp/exception-specifications-throw-cpp.md) 。

通过使用来避免此警告[警告](../../preprocessor/warning.md)杂注：

```
#pragma warning( disable : 4290 )
```

下面的代码示例生成 C4290:

```
// C4290.cpp
// compile with: /EHs /W3 /c
void f1(void) throw(int) {}   // C4290

// OK
void f2(void) throw() {}
void f3(void) throw(...) {}
```
---
title: 编译器警告（等级 3）C4290
ms.date: 11/04/2016
f1_keywords:
- C4290
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
ms.openlocfilehash: 5970aa439a450bda4c1a2036da299d5c3cfbdb7a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198895"
---
# <a name="compiler-warning-level-3-c4290"></a>编译器警告（等级 3）C4290

C++已忽略异常规范，但指示函数未 __declspec （nothrow）

函数是使用异常规范声明的，它的C++视觉对象接受但不实现。 在编译过程中忽略具有异常规范的代码可能需要重新编译和链接，以便在支持异常规范的未来版本中重复使用。

有关详细信息，请参阅[异常规范（throw）](../../cpp/exception-specifications-throw-cpp.md) 。

可以通过使用[警告](../../preprocessor/warning.md)杂注来避免此警告：

```cpp
#pragma warning( disable : 4290 )
```

下面的代码示例生成 C4290：

```cpp
// C4290.cpp
// compile with: /EHs /W3 /c
void f1(void) throw(int) {}   // C4290

// OK
void f2(void) throw() {}
void f3(void) throw(...) {}
```

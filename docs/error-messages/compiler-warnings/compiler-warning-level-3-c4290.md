---
title: 编译器警告（等级3） C4290
ms.date: 11/04/2016
f1_keywords:
- C4290
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
ms.openlocfilehash: 5ccacd7d5f4dfd2e9ad8de3958d7aa43571091fe
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051652"
---
# <a name="compiler-warning-level-3-c4290"></a>编译器警告（等级3） C4290

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
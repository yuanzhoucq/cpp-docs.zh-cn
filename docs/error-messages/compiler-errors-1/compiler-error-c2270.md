---
title: 编译器错误 C2270
ms.date: 11/04/2016
f1_keywords:
- C2270
helpviewer_keywords:
- C2270
ms.assetid: b52c068e-0b61-42e7-b775-4d57b3ddcba0
ms.openlocfilehash: 704d397f06432575b7db531039b4454d4716c54e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388912"
---
# <a name="compiler-error-c2270"></a>编译器错误 C2270

function： 非成员函数上不允许修饰符

使用声明非成员函数[const](../../cpp/const-cpp.md)，[易失性](../../cpp/volatile-cpp.md)，或另一个内存模型修饰符。

下面的示例生成 C2270:

```
// C2270.cpp
// compile with: /c
void func1(void) const;   // C2270, nonmember function

void func2(void);

class CMyClass {
public:
   void func2(void) const;
};
```
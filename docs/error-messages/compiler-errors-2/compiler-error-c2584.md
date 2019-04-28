---
title: 编译器错误 C2584
ms.date: 11/04/2016
f1_keywords:
- C2584
helpviewer_keywords:
- C2584
ms.assetid: 836e2c0a-86c0-4742-b432-beb0191ad20e
ms.openlocfilehash: b61ad65555b5d5232468206f6170223c5f160a34
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360460"
---
# <a name="compiler-error-c2584"></a>编译器错误 C2584

Class： 直接基 Base2 不可访问;已 Base1 的基

`Class` 直接从已派生`Base1`。 `Base2` 此外派生`Base1`。 `Class` 不能从派生`Base2`因为这可能意味着 （间接） 继承`Base1`同样，这是不合法因为`Base1`已直接基类。

## <a name="example"></a>示例

下面的示例生成 C2584。

```
// C2584.cpp
// compile with: /c
struct A1 {
   virtual int MyFunction();
};

struct A2 {
    virtual int MyFunction();
};

struct B1: public virtual A1, virtual A2 {
    virtual int MyFunction();
};

struct B2: public virtual A2, virtual A1 {
    virtual int MyFunction();
};

struct C: virtual B1, B2 {
    virtual int MyFunction();
};

struct Z : virtual B2, virtual C {   // C2584
// try the following line insted
// struct Z : virtual C {
    virtual int MyFunction();
};
```
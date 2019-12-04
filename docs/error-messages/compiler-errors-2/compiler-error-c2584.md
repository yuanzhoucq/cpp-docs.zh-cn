---
title: 编译器错误 C2584
ms.date: 11/04/2016
f1_keywords:
- C2584
helpviewer_keywords:
- C2584
ms.assetid: 836e2c0a-86c0-4742-b432-beb0191ad20e
ms.openlocfilehash: 2c3b10ecd6808ccd864ecf877fe9f1d0e9f30a3a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748627"
---
# <a name="compiler-error-c2584"></a>编译器错误 C2584

"Class"：无法访问直接基 "Base2";已是 "Base1" 的基

`Class` 已直接从 `Base1`派生。 `Base2` 也派生自 `Base1`。 `Class` 无法从 `Base2` 派生，因为这将意味着再次从 `Base1` 继承（间接），这是不合法的，因为 `Base1` 已经是直接基类。

## <a name="example"></a>示例

下面的示例生成 C2584。

```cpp
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

---
title: 编译器错误 C2584 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2584
dev_langs:
- C++
helpviewer_keywords:
- C2584
ms.assetid: 836e2c0a-86c0-4742-b432-beb0191ad20e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0f8c523936473673f3af09400922e2594ed1891
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029424"
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
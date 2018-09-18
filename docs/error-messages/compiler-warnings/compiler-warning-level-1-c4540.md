---
title: 编译器警告 （等级 1） C4540 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4540
dev_langs:
- C++
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e3f553bd1f910c7b17e079dc1f03664c78383e3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042762"
---
# <a name="compiler-warning-level-1-c4540"></a>编译器警告（等级 1）C4540

dynamic_cast 用于转换为不可访问或不明确的基;运行时测试将失败 (类型 type1 到 type2)

您使用`dynamic_cast`将从一种类型转换为另一个。 编译器确定强制转换会总是失败 (返回**NULL**) 因为基类不可访问 (`private`，例如) 或不明确 （例如在类层次结构中出现不止一次）。

下面显示了此警告的示例。 类**B**派生自类**A**。该程序使用`dynamic_cast`若要从类转换**B** （派生的类） 到类**一个**，其始终会失败，因为类**B**是`private`，因此无法访问。 正在更改的访问权限**A**到**公共**将解决此警告。

```
// C4540.cpp
// compile with: /W1

struct A {
   virtual void g() {}
};

struct B : private A {
   virtual void g() {}
};

int main() {
   B b;
   A * ap = dynamic_cast<A*>(&b);   // C4540
}
```
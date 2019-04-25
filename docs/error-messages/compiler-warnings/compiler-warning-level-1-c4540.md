---
title: 编译器警告（等级 1）C4540
ms.date: 11/04/2016
f1_keywords:
- C4540
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
ms.openlocfilehash: 86f6cd866f7708277ebba436ba7c076086dc9c8c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160700"
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
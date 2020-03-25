---
title: 编译器警告（等级 1）C4540
ms.date: 11/04/2016
f1_keywords:
- C4540
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
ms.openlocfilehash: 859ff75bbd4b3fe248d9658495e64c0c039fbb40
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186408"
---
# <a name="compiler-warning-level-1-c4540"></a>编译器警告（等级 1）C4540

dynamic_cast 用于转换为不可访问或不明确的基;运行时测试将失败（"type1" 到 "type2"）

你使用 `dynamic_cast` 从一种类型转换为另一种类型。 编译器确定转换将始终失败（返回**NULL**），因为基类不可访问（例如`private`）或不明确（例如，在类层次结构中多次出现）。

下面显示了此警告的示例。 类**B**派生自类**A**。程序使用 `dynamic_cast` 从类**b** （派生类）强制转换为类**A**，这将始终失败，因为类**b** `private`，因而无法访问。 将**对的访问权限更改为 "** **公共**" 将解决此警告。

```cpp
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

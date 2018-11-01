---
title: 编译器错误 C3185
ms.date: 11/04/2016
f1_keywords:
- C3185
helpviewer_keywords:
- C3185
ms.assetid: 5bf96279-043c-4981-9d02-b4550071b192
ms.openlocfilehash: db448b462cd3a3f325c529e730e5c8f65e2b8f51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598804"
---
# <a name="compiler-error-c3185"></a>编译器错误 C3185

在托管或 WinRT 类型“type”上使用了“typeid”，请改用“operator”

无法应用[typeid](../../cpp/typeid-operator.md)运算符为托管或 WinRT 类型; 请改用[typeid](../../windows/typeid-cpp-component-extensions.md)相反。

下面的示例生成 C3185，并演示如何修复此错误：

```
// C3185a.cpp
// compile with: /clr
ref class Base {};
ref class Derived : public Base {};

int main() {
   Derived ^ pd = gcnew Derived;
   Base ^pb = pd;
   const type_info & t1 = typeid(pb);   // C3185
   System::Type ^ MyType = Base::typeid;   // OK
};
```

---
title: 编译器错误 C3185
ms.date: 11/04/2016
f1_keywords:
- C3185
helpviewer_keywords:
- C3185
ms.assetid: 5bf96279-043c-4981-9d02-b4550071b192
ms.openlocfilehash: 45afe70b454f72dd8c9b8ce9771ce1f5aef6a10e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366077"
---
# <a name="compiler-error-c3185"></a>编译器错误 C3185

在托管或 WinRT 类型“type”上使用了“typeid”，请改用“operator”

无法应用[typeid](../../cpp/typeid-operator.md)运算符为托管或 WinRT 类型; 请改用[typeid](../../extensions/typeid-cpp-component-extensions.md)相反。

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

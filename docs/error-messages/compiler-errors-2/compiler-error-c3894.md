---
title: 编译器错误 C3894 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3894
dev_langs:
- C++
helpviewer_keywords:
- C3894
ms.assetid: 6d5ac903-1dea-431d-8e3a-cebca4342983
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 373da78257ee0f5ce7307ab521cccb0297933240
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080085"
---
# <a name="compiler-error-c3894"></a>编译器错误 C3894

var： 类 class 的类构造函数中只允许 initonly 静态数据成员的左值使用

静态[initonly](../../dotnet/initonly-cpp-cli.md)数据成员只能用作其时刻的声明，或在静态构造函数中的左值。

实例 （非静态） initonly 数据成员仅可用作其时刻的声明，或在实例 （非静态） 构造函数中的左值。

下面的示例生成 C3894:

```
// C3894.cpp
// compile with: /clr
ref struct Y1 {
   initonly static int data_var = 0;

public:
   // class constructor
   static Y1() {
      data_var = 99;   // OK
      System::Console::WriteLine("in static constructor");
   }

   // not the class constructor
   Y1(int i) {
      data_var = i;   // C3894
   }

   static void Test() {}

};

int main() {
   Y1::data_var = 88;   // C3894
   int i = Y1::data_var;
   Y1 ^ MyY1 = gcnew Y1(99);
   Y1::Test();
}
```
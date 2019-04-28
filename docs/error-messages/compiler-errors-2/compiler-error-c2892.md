---
title: 编译器错误 C2892
ms.date: 11/04/2016
f1_keywords:
- C2892
helpviewer_keywords:
- C2892
ms.assetid: c22a5084-2f50-42c2-a56b-6dfe5442edc9
ms.openlocfilehash: 296224532b19d9ff85c8644aa653b6d842205213
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62265875"
---
# <a name="compiler-error-c2892"></a>编译器错误 C2892

局部类不应有成员模板

模板成员函数不能在函数中定义的类中。

下面的示例生成 C2892:

```
// C2892.cpp
int main() {
   struct local {
      template<class T>   // C2892
      void f() {}
   };
}
```
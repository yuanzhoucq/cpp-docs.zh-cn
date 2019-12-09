---
title: 编译器错误 C2589
ms.date: 11/04/2016
f1_keywords:
- C2589
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
ms.openlocfilehash: 76cc35e57c1577ed23c043740f37c602600da542
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748497"
---
# <a name="compiler-error-c2589"></a>编译器错误 C2589

"identifier"： "：：" 右边的非法标记

如果类、结构或联合名称出现在范围解析运算符（双冒号）的左侧，则右侧的标记必须是类、结构或联合成员。 否则，任何全局标识符都可以出现在右侧。

无法重载范围解析运算符。

下面的示例生成 C2589：

```cpp
// C2589.cpp
void Test(){}
class A {};
void operator :: ();   // C2589

int main() {
   ::Test();
}
```

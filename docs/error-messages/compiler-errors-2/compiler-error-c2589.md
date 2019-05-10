---
title: 编译器错误 C2589
ms.date: 11/04/2016
f1_keywords:
- C2589
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
ms.openlocfilehash: 18d8f7130c34f5e1e33bc7aa9b9463f50c243045
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386936"
---
# <a name="compiler-error-c2589"></a>编译器错误 C2589

identifier： 非法标记在右侧::

如果类、 结构或联合名称显示在范围解析运算符 （双冒号） 的左侧，在右侧的标记必须是类、 结构或联合成员。 否则，任何全局标识符可以显示在右侧。

范围解析运算符无法进行重载。

下面的示例生成 C2589:

```
// C2589.cpp
void Test(){}
class A {};
void operator :: ();   // C2589

int main() {
   ::Test();
}
```
---
title: 编译器错误 C2589 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2589
dev_langs:
- C++
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2db5dde898a3e5918eed62b2b32231b5d7ed014f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046051"
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
---
title: 编译器错误 C3153
ms.date: 11/04/2016
f1_keywords:
- C3153
helpviewer_keywords:
- C3153
ms.assetid: d775d97e-2480-484f-81f1-88406b10f947
ms.openlocfilehash: 54fa7de8eb3df8d4b3695544c5285cc202275492
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745910"
---
# <a name="compiler-error-c3153"></a>编译器错误 C3153

"interface"：不能创建接口的实例

接口不能实例化。 若要使用接口的成员，请从接口派生一个类，实现接口成员，然后使用成员。

下面的示例生成 C3153：

```cpp
// C3153.cpp
// compile with: /clr
interface class A {
};

int main() {
   A^ a = gcnew A;   // C3153
}
```

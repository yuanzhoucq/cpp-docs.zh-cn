---
title: 编译器错误 C3072
ms.date: 11/04/2016
f1_keywords:
- C3072
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
ms.openlocfilehash: a8fe0802a7529551fce1c0b7242c867db52d8842
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756755"
---
# <a name="compiler-error-c3072"></a>编译器错误 C3072

运算符 "operator" 不能应用于 ref 类的实例

使用一元 "`operator`" 运算符将 ref 类的实例转换为句柄类型

CLR 类型需要 CLR 运算符，而不是本机（或标准）运算符。  有关详细信息，请参阅[跟踪引用运算符](../../extensions/tracking-reference-operator-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3072。

```cpp
// C3072.cpp
// compile with: /clr
ref class R {};

int main() {
   R r1;
   R^ r2 = &r1;   // C3072
   R^ r3 = %r1;   // OK
}
```

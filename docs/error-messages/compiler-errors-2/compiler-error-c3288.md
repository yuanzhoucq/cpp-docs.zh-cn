---
title: 编译器错误 C3288
ms.date: 11/04/2016
f1_keywords:
- C3288
helpviewer_keywords:
- C3288
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
ms.openlocfilehash: a7b87fdbd2e15906ebc0c669f0b9a74ebf97f0b3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760174"
---
# <a name="compiler-error-c3288"></a>编译器错误 C3288

"type"：非法取消对句柄类型的引用

编译器检测到非法取消对句柄类型的引用。 您可以取消引用句柄类型并将其分配给引用。 有关详细信息，请参阅[跟踪引用运算符](../../extensions/tracking-reference-operator-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3288。

```cpp
// C3288.cpp
// compile with: /clr
ref class R {};
int main() {
   *(System::Object^) nullptr;   // C3288

// OK
   (System::Object^) nullptr;   // OK
   R^ r;
   R% pr = *r;
}
```

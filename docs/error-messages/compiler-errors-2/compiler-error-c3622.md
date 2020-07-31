---
title: 编译器错误 C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: 8775ff6fd78f1092ae931921a2b15ed2f8b166e9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214537"
---
# <a name="compiler-error-c3622"></a>编译器错误 C3622

"class"：声明为 "关键字" 的类不能实例化

尝试实例化标记为[抽象](../../extensions/abstract-cpp-component-extensions.md)的类。 标记为的类 **`abstract`** 可以是基类，但无法对其进行实例化。

## <a name="example"></a>示例

下面的示例生成 C3622。

```cpp
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```

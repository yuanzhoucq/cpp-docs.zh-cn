---
title: 编译器错误 C3189
ms.date: 11/04/2016
f1_keywords:
- C3189
helpviewer_keywords:
- C3189
ms.assetid: b254de79-931e-4a59-a9f4-1c690d90ca5e
ms.openlocfilehash: fe9dc38748fd667734c5d80f1284348184fed450
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456974"
---
# <a name="compiler-error-c3189"></a>编译器错误 C3189

typeid\<键入抽象声明符 >： 不再支持此语法，请使用:: typeid 改为

过时形式[typeid](../../windows/typeid-cpp-component-extensions.md)已使用，使用新的窗体。

下面的示例生成 C3189:

```
// C3189.cpp
// compile with: /clr
int main() {
   System::Type^ t  = typeid<System::Object>;   // C3189
   System::Type^ t2  = System::Object::typeid;   // OK
}
```
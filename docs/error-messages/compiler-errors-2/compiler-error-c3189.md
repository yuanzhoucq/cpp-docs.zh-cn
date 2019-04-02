---
title: 编译器错误 C3189
ms.date: 11/04/2016
f1_keywords:
- C3189
helpviewer_keywords:
- C3189
ms.assetid: b254de79-931e-4a59-a9f4-1c690d90ca5e
ms.openlocfilehash: b2de290178657ae427b5ad7999c511ae7ff9f1eb
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781882"
---
# <a name="compiler-error-c3189"></a>编译器错误 C3189

typeid\<键入抽象声明符 >： 不再支持此语法，请使用:: typeid 改为

过时形式[typeid](../../extensions/typeid-cpp-component-extensions.md)已使用，使用新的窗体。

下面的示例生成 C3189:

```
// C3189.cpp
// compile with: /clr
int main() {
   System::Type^ t  = typeid<System::Object>;   // C3189
   System::Type^ t2  = System::Object::typeid;   // OK
}
```
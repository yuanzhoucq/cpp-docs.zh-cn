---
title: 编译器错误 C3804 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3804
dev_langs:
- C++
helpviewer_keywords:
- C3804
ms.assetid: 7c4cda28-ec96-4d04-937b-36dbd9944722
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ef798ec8697ee9a856162b9aa63ccbf23db15f7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113196"
---
# <a name="compiler-error-c3804"></a>编译器错误 C3804

property_accessor： 访问器方法的属性必须是全部静态或所有非静态

访问器函数时定义非 trivial 属性，可以是静态或实例，但不可同时使用两者。

有关更多信息，请参见 [property](../../windows/property-cpp-component-extensions.md) 。

## <a name="example"></a>示例

下面的示例生成 C3804。

```
// C3804.cpp
// compile with: /c /clr
ref struct A {

   property int i {
      static int get() {}
      void set(int i) {}
   }   // C3804 error

   // OK
   property int j {
      int get() { return 0; }
      void set(int i) {}
   }

   property int k {
      static int get() { return 0; }
      static void set(int i) {}
   }
};
```
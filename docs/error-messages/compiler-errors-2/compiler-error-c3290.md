---
title: 编译器错误 C3290 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3290
dev_langs:
- C++
helpviewer_keywords:
- C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b97818dd6ef7b38bb815e2c0a6345cc056fc45c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058921"
---
# <a name="compiler-error-c3290"></a>编译器错误 C3290

“type”: 普通属性不能具有引用类型

未正确声明属性。 当声明普通属性时，编译器创建一个此属性将更新的变量，类中不能有跟踪引用变量。

请参阅[属性](../../windows/property-cpp-component-extensions.md)并[跟踪引用运算符](../../windows/tracking-reference-operator-cpp-component-extensions.md)有关详细信息。

## <a name="example"></a>示例

下面的示例生成 C3290。

```
// C3290.cpp
// compile with: /clr /c
ref struct R {};

ref struct X {
   R^ mr;

   property R % y;   // C3290
   property R ^ x;   // OK

   // OK
   property R% prop {
      R% get() {
         return *mr;
      }

      void set(R%) {}
   }
};

int main() {
   X x;
   R% xp = x.prop;
}
```
---
title: 编译器错误 C3288 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3288
dev_langs:
- C++
helpviewer_keywords:
- C3288
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36412510efcedd765ad44b4aab61e6a7d64155fb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079929"
---
# <a name="compiler-error-c3288"></a>编译器错误 C3288

type： 非法取消对引用的句柄类型

编译器检测到非法取消引用的句柄类型。 可以取消引用句柄类型并将其分配给一个引用。 有关详细信息，请参阅[跟踪引用运算符](../../windows/tracking-reference-operator-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3288。

```
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
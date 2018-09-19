---
title: 编译器错误 C3072 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3072
dev_langs:
- C++
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a36eaaf12cf9f8909455847036f670f6fc0cd40b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047507"
---
# <a name="compiler-error-c3072"></a>编译器错误 C3072

运算符 operator 无法应用于 ref 类的实例

使用一元`operator`运算符将 ref 类的实例转换为句柄类型

CLR 类型需要 CLR 运算符，不能使用本机 （或标准） 运算符。  有关详细信息，请参阅[跟踪引用运算符](../../windows/tracking-reference-operator-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3072。

```
// C3072.cpp
// compile with: /clr
ref class R {};

int main() {
   R r1;
   R^ r2 = &r1;   // C3072
   R^ r3 = %r1;   // OK
}
```
---
title: 编译器错误 C2299 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2299
dev_langs:
- C++
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4977f4a5ac81cf4c04d3b143f6f7e670a9d9279
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049613"
---
# <a name="compiler-error-c2299"></a>编译器错误 C2299

function： 行为更改： 显式专用化不能复制构造函数或复制赋值运算符

此外可以为 Visual c + + 2005年执行的编译器一致性工作生成此错误： 以前版本的 Visual c + + 允许复制构造函数或复制赋值运算符的显式专用化。

若要解决 C2299，请不要复制构造函数或赋值运算符的模板函数，但而不是采用类类型的非模板函数。 通过显式指定模板自变量调用复制构造函数或赋值运算符的任何代码需要删除模板自变量。

下面的示例生成 C2299:

```
// C2299.cpp
// compile with: /c
class C {
   template <class T>
   C (T t);

   template <> C (const C&);   // C2299
   C (const C&);   // OK
};
```
---
title: 编译器错误 C2833 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2833
dev_langs:
- C++
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53360c1eaf81ad407589fbdb125d9e6fe017708e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070166"
---
# <a name="compiler-error-c2833"></a>编译器错误 C2833

operator operator 不是可识别的运算符或类型

Word`operator`后面必须有你想要替代的运算符或你想要转换的类型。

可以在托管类型中定义的运算符的列表，请参阅[用户定义的运算符](../../dotnet/user-defined-operators-cpp-cli.md)。

下面的示例生成 C2833:

```
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```
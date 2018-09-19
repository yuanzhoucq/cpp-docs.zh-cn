---
title: 编译器错误 C3176 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3176
dev_langs:
- C++
helpviewer_keywords:
- C3176
ms.assetid: 6cc8d602-8e15-47a7-b1b5-e93e5d50e271
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa2ec269061531688620b89279a9670982c72578
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104177"
---
# <a name="compiler-error-c3176"></a>编译器错误 C3176

type： 不能声明局部值类型

只能在全局范围内的值类型作为声明一个类。

## <a name="example"></a>示例

下面的示例生成 C3176。

```
// C3176.cpp
// compile with: /clr
int main () {
   enum class C {};   // C3176
}
```
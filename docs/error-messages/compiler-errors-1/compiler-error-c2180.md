---
title: 编译器错误 C2180 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2180
dev_langs:
- C++
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c74912b92162cbfcada3630ed6a6845b67045d0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084141"
---
# <a name="compiler-error-c2180"></a>编译器错误 C2180

控制表达式具有类型“type”

`if`、`while`、`for` 或 `do` 语句中的控制表达式是强制转换为 `void` 的表达式。 若要解决此问题，请将控制表达式更改为生成 `bool` 的表达式或更改为可以转换为 `bool` 的类型。

以下示例生成 C2180：

```
// C2180.c

int main() {
   while ((void)1)   // C2180
      return 1;
   while (1)         // OK
      return 0;
}
```
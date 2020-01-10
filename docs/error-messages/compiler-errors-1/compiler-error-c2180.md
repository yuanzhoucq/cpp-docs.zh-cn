---
title: 编译器错误 C2180
ms.date: 11/04/2016
f1_keywords:
- C2180
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
ms.openlocfilehash: 5e9444356e536a8369dbcf62cac3c7538d9da5dd
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301894"
---
# <a name="compiler-error-c2180"></a>编译器错误 C2180

控制表达式具有类型“type”

`if`、`while`、`for` 或 `do` 语句中的控制表达式是强制转换为 `void` 的表达式。 若要解决此问题，请将控制表达式更改为生成 `bool` 的表达式或更改为可以转换为 `bool` 的类型。

以下示例生成 C2180：

```c
// C2180.c

int main() {
   while ((void)1)   // C2180
      return 1;
   while (1)         // OK
      return 0;
}
```

---
title: 编译器错误 C2180
ms.date: 11/04/2016
f1_keywords:
- C2180
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
ms.openlocfilehash: 3794a1ce0fcbe60c06cb3efca45a3081e85c17ce
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87210015"
---
# <a name="compiler-error-c2180"></a>编译器错误 C2180

控制表达式具有类型“type”

**`if`**、、或语句中的控制表达式 **`while`** **`for`** **`do`** 是强制转换为的表达式 **`void`** 。 若要解决此问题，请将控制表达式更改为一个生成 **`bool`** 或可转换为的类型的 **`bool`** 。

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

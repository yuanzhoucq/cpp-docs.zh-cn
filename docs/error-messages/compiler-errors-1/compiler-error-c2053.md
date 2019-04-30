---
title: 编译器错误 C2053
ms.date: 11/04/2016
f1_keywords:
- C2053
helpviewer_keywords:
- C2053
ms.assetid: 13324c85-13a8-4996-bd42-a31bfe7ff80f
ms.openlocfilehash: be5517ce77872fe395a52c5b1e0070612e205a3d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408779"
---
# <a name="compiler-error-c2053"></a>编译器错误 C2053

identifier： 宽字符串不匹配

宽字符串分配给不兼容的类型。

下面的示例生成 C2053:

```
// C2053.c
int main() {
   char array[] = L"Rika";   // C2053
}
```
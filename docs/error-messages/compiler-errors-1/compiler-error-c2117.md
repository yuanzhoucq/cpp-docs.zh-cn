---
title: 编译器错误 C2117
ms.date: 11/04/2016
f1_keywords:
- C2117
helpviewer_keywords:
- C2117
ms.assetid: b947379d-5861-42fc-ac26-170318579cbd
ms.openlocfilehash: 2f6a1e26972f093e50c5e655935f750195ab7d3b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338566"
---
# <a name="compiler-error-c2117"></a>编译器错误 C2117

identifier： 数组界限溢出

数组具有初始值设定项太多：

- 数组元素和初始值设定项在大小和数量不匹配。

- Null 终止符的字符串中的没有空间。

下面的示例生成 C2117:

```
// C2117.cpp
int main() {
   char abc[4] = "abcd";   // C2117
   char def[4] = "abd";   // OK
}
```
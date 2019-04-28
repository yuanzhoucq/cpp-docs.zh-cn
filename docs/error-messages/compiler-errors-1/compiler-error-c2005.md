---
title: 编译器错误 C2005
ms.date: 11/04/2016
f1_keywords:
- C2005
helpviewer_keywords:
- C2005
ms.assetid: 090530ed-e0ec-4358-833a-ca24260e7ffe
ms.openlocfilehash: 49d0375d5733410d728797d2a881075377b33ba6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208992"
---
# <a name="compiler-error-c2005"></a>编译器错误 C2005

\#行的预期行号，找到 token

`#line`指令后面必须跟一个行号。

下面的示例生成 C2005:

```
// C2005.cpp
int main() {
   int i = 0;
   #line i   // C2005
}
```

可能的解决方法：

```
// C2005b.cpp
int main() {
   int i = 0;
   #line 0
}
```
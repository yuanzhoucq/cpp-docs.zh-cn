---
title: 编译器错误 C2005 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2005
dev_langs:
- C++
helpviewer_keywords:
- C2005
ms.assetid: 090530ed-e0ec-4358-833a-ca24260e7ffe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6dfba3b960a046bf40751c135c3b99fbe843545
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100664"
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
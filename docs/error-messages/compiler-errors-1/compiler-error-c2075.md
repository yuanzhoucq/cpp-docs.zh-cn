---
title: 编译器错误 C2075 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2075
dev_langs:
- C++
helpviewer_keywords:
- C2075
ms.assetid: 8b1865d2-540b-4117-b982-e7a58a0b6cf7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ffedc5ce0ae073d53c32f6d0b9447987da31391a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083023"
---
# <a name="compiler-error-c2075"></a>编译器错误 C2075

“identifier”：数组初始化需要大括号

指定的数组两边没有大括号。

以下示例生成 C2075：

```
// C2075.c
int main() {
   int i[] = 1, 2, 3 };   // C2075
}
```

可能的解决方法：

```
// C2075b.c
int main() {
   int j[] = { 1, 2, 3 };
}
```
---
title: 编译器错误 C2008
ms.date: 11/04/2016
f1_keywords:
- C2008
helpviewer_keywords:
- C2008
ms.assetid: e748ccbe-ffd4-4008-aca7-e53c25225209
ms.openlocfilehash: 292f5c6ab9a4e14077f848ff57ff08adefeb09a1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757327"
---
# <a name="compiler-error-c2008"></a>编译器错误 C2008

“character”: 宏定义中的意外

紧跟在宏名称之后的字符。 若要解决此错误，宏名称后必须有一个空格。

下面的示例生成 C2008：

```cpp
// C2008.cpp
#define TEST1"mytest1"    // C2008
```

可能的解决方法：

```cpp
// C2008b.cpp
// compile with: /c
#define TEST2 "mytest2"
```

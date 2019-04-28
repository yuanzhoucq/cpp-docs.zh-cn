---
title: 编译器错误 C2008
ms.date: 11/04/2016
f1_keywords:
- C2008
helpviewer_keywords:
- C2008
ms.assetid: e748ccbe-ffd4-4008-aca7-e53c25225209
ms.openlocfilehash: 0bd9193d6e305a4b6c6851ef2524a68ecc056816
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208979"
---
# <a name="compiler-error-c2008"></a>编译器错误 C2008

“character”: 宏定义中的意外

在紧靠宏名称之后出现的字符。 若要解决此错误，必须有一个空格后宏名称。

下面的示例生成 C2008:

```
// C2008.cpp
#define TEST1"mytest1"    // C2008
```

可能的解决方法：

```
// C2008b.cpp
// compile with: /c
#define TEST2 "mytest2"
```
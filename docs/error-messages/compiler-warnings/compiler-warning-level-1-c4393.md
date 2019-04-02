---
title: 编译器警告（等级 1）C4393
ms.date: 11/04/2016
f1_keywords:
- C4393
helpviewer_keywords:
- C4393
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
ms.openlocfilehash: 4226c8ecd41e890d70fa5741decae605d45b620f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58768986"
---
# <a name="compiler-warning-level-1-c4393"></a>编译器警告（等级 1）C4393

var： 常量不会影响 literal 数据成员;忽略

一个[文字](../../extensions/literal-cpp-component-extensions.md)数据成员也被指定为常量。  Literal 数据成员暗指常量，因为您不需要添加到声明 const。

下面的示例生成 C4393:

```
// C4393.cpp
// compile with: /clr /W1 /c
ref struct Y1 {
   literal const int staticConst = 10;   // C4393
   literal int staticConst2 = 10;   // OK
};
```
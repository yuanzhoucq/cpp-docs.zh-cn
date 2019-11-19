---
title: 编译器警告（等级1） C4393
ms.date: 11/04/2016
f1_keywords:
- C4393
helpviewer_keywords:
- C4393
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
ms.openlocfilehash: 92cb9a063a2f6e4660c3f84516527c1417c55e46
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966138"
---
# <a name="compiler-warning-level-1-c4393"></a>编译器警告（等级1） C4393

"var"：常量不会影响 literal 数据成员;掉

[文本](../../extensions/literal-cpp-component-extensions.md)数据成员也被指定为 const。  由于文本数据成员隐含为 const，因此不需要将常量添加到声明。

下面的示例生成 C4393：

```cpp
// C4393.cpp
// compile with: /clr /W1 /c
ref struct Y1 {
   literal const int staticConst = 10;   // C4393
   literal int staticConst2 = 10;   // OK
};
```
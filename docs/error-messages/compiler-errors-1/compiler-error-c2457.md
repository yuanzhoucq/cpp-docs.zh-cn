---
title: 编译器错误 C2457
ms.date: 11/04/2016
f1_keywords:
- C2457
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
ms.openlocfilehash: a08ac9f9cfbc332b90ad16c663349ee227427278
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446627"
---
# <a name="compiler-error-c2457"></a>编译器错误 C2457

> '*宏*： 预定义的宏不能出现在函数体的外部

尝试使用预定义的宏，如[ &#95;&#95;函数&#95;&#95;](../../preprocessor/predefined-macros.md)，在全局空间中。

## <a name="example"></a>示例

下面的示例生成 C2457，并还显示了正确的使用：

```cpp
// C2457.cpp
#include <stdio.h>

__FUNCTION__;   // C2457, cannot be global

int main()
{
    printf_s("\n%s", __FUNCTION__);   // OK
}
```
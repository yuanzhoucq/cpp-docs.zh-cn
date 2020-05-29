---
title: 编译器错误 C2457
ms.date: 11/04/2016
f1_keywords:
- C2457
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
ms.openlocfilehash: 40e666b1f2b566ca6309ee7759452647f8101a38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205239"
---
# <a name="compiler-error-c2457"></a>编译器错误 C2457

> "*宏*"：预定义的宏不能出现在函数体的外部

尝试在全局空间中使用预定义的宏，如[ &#95; &#95;函数&#95;](../../preprocessor/predefined-macros.md)。

## <a name="example"></a>示例

下面的示例生成 C2457，并显示正确的用法：

```cpp
// C2457.cpp
#include <stdio.h>

__FUNCTION__;   // C2457, cannot be global

int main()
{
    printf_s("\n%s", __FUNCTION__);   // OK
}
```

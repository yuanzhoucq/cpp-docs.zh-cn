---
title: 编译器错误 C2457 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2457
dev_langs:
- C++
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 61cdb4f4b679bab858717a6fb96838f389822a6b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33224918"
---
# <a name="compiler-error-c2457"></a>编译器错误 C2457

> *宏*： 预定义的宏不能出现在函数体外部

您尝试使用预定义的宏，如[ &#95;&#95;函数&#95;&#95;](../../preprocessor/predefined-macros.md)，在全局空间中。

## <a name="example"></a>示例

下面的示例生成 C2457，并还显示正确用法：

```cpp
// C2457.cpp
#include <stdio.h>

__FUNCTION__;   // C2457, cannot be global

int main()
{
    printf_s("\n%s", __FUNCTION__);   // OK
}
```
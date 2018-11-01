---
title: 编译器错误 C2097
ms.date: 11/04/2016
f1_keywords:
- C2097
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
ms.openlocfilehash: 8b50221997dcf2fb60ee2b82ed630dd325a38145
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676585"
---
# <a name="compiler-error-c2097"></a>编译器错误 C2097

初始化非法

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 使用非常量值的变量的初始化。

1. 具有一长串地址的短地址的初始化。

1. 初始化的局部结构、 联合或数组时，用非常量表达式进行编译 **/Za**。

1. 使用包含逗号运算符的表达式进行初始化。

1. 使用一个表达式，不是常量或符号的初始化。
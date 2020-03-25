---
title: 编译器错误 C2097
ms.date: 11/04/2016
f1_keywords:
- C2097
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
ms.openlocfilehash: cdb14aeef61d136a6992a05a72f382e589e88770
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207489"
---
# <a name="compiler-error-c2097"></a>编译器错误 C2097

非法初始化

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 使用非常量值初始化变量。

1. 使用长地址初始化短地址。

1. 使用 **/za**进行编译时，使用非常量表达式初始化本地结构、联合或数组。

1. 使用包含逗号运算符的表达式进行初始化。

1. 使用既不是常量也不是符号的表达式进行初始化。

---
title: 编译器错误 C2097 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2097
dev_langs:
- C++
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2da955f5382a1ebacdb507a69ed02627b11462e5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021858"
---
# <a name="compiler-error-c2097"></a>编译器错误 C2097

初始化非法

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 使用非常量值的变量的初始化。

1. 具有一长串地址的短地址的初始化。

1. 初始化的局部结构、 联合或数组时，用非常量表达式进行编译 **/Za**。

1. 使用包含逗号运算符的表达式进行初始化。

1. 使用一个表达式，不是常量或符号的初始化。
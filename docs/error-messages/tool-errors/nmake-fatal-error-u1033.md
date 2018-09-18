---
title: NMAKE 错误 U1033 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1033
dev_langs:
- C++
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7492e5fd77f8e88b2191174f84c298c6166d8d89
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066371"
---
# <a name="nmake-fatal-error-u1033"></a>NMAKE 错误 U1033

语法错误: string 意外

字符串不是生成文件的有效语法的一部分。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 如果右尖括号组 (**<<**) 有关内联文件不在行开头，将发生以下错误：

    ```
    syntax error : 'EOF' unexpected
    ```

1. 如果宏定义中生成文件中包含的等号 (**=**) 没有前面名，或者如果正在定义的名称是扩展到 nothing 的宏，将出现以下错误：

    ```
    syntax error : '=' unexpected
    ```

1. 如果以分号 (**;**) 工具中的注释行中。INI 不在开头的行，将出现以下错误：

    ```
    syntax error : ';' unexpected
    ```

1. 如果已设置生成文件格式的字处理器中，会出现下列错误：

    ```
    syntax error : ':' unexpected
    ```
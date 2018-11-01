---
title: NMAKE 错误 U1033
ms.date: 11/04/2016
f1_keywords:
- U1033
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
ms.openlocfilehash: 3b1df28e3cd7b27a9e7a130d9d71c1af68db9aec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445235"
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
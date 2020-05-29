---
title: NMAKE 错误 U1033
ms.date: 11/04/2016
f1_keywords:
- U1033
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
ms.openlocfilehash: 4511b15c84479c3531a3bea85964e2768de0181f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173382"
---
# <a name="nmake-fatal-error-u1033"></a>NMAKE 错误 U1033

语法错误：意外的 "string"

该字符串不是生成文件的有效语法的一部分。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 如果内联文件的右尖括号集（ **<<** ）不在行首，则会发生以下错误：

    ```
    syntax error : 'EOF' unexpected
    ```

1. 如果生成文件中的宏定义包含一个没有前面名称的等号（ **=** ），或者如果要定义的名称是一个扩展为 nothing 的宏，则会发生以下错误：

    ```
    syntax error : '=' unexpected
    ```

1. 如果工具的注释行中的分号（ **;** ）。INI 不在行的开头，出现以下错误：

    ```
    syntax error : ';' unexpected
    ```

1. 如果生成文件已由字处理程序设置格式，则可能会发生以下错误：

    ```
    syntax error : ':' unexpected
    ```

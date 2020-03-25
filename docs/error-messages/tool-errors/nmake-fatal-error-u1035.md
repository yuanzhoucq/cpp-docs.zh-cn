---
title: NMAKE 错误 U1035
ms.date: 11/04/2016
f1_keywords:
- U1035
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
ms.openlocfilehash: 3eda424574dfa48901cf4dc6aea3b28beb739dc0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193714"
---
# <a name="nmake-fatal-error-u1035"></a>NMAKE 错误 U1035

语法错误：应输入 "：" 或 "=" 分隔符

应为冒号（ **：** ）或等号（ **=** ）。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 冒号不在目标之后。

1. 冒号和无空格（如：）后跟单字母目标。 NMAKE 将它解释为驱动器规格。

1. 冒号不遵循推理规则。

1. 宏定义后面没有等号。

1. 一个字符，后面跟一个用于将命令继续到新行的反斜杠（ **\\** ）。

1. 出现的字符串不遵循任何 NMAKE 语法规则。

1. 生成文件由字处理器进行了格式设置。

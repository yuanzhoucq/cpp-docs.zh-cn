---
title: NMAKE 错误 U1035
ms.date: 11/04/2016
f1_keywords:
- U1035
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
ms.openlocfilehash: 9c4055bb99243f7d20c1da90aef7b916c46c2749
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589472"
---
# <a name="nmake-fatal-error-u1035"></a>NMAKE 错误 U1035

语法错误： 预期: 或 = 分隔符

冒号 (**:**) 或等号 (**=**) 应。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 冒号不遵循目标。

1. 冒号和没有空格 （例如 a:） 后接单个字母目标。 NMAKE 解释它为驱动器规格。

1. 冒号不遵循推理规则。

1. 通过等号后面不是宏定义。

1. 字符跟一个反斜杠 (**\\**) 用于将命令继续到新行。

1. 一个字符串出现的不遵循任何 NMAKE 语法规则。

1. 生成文件格式化的字处理器。
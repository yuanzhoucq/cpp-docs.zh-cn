---
title: NMAKE 错误 U1035 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1035
dev_langs:
- C++
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0383bf4742d637d669070efa5370ebda0c7ab159
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019849"
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
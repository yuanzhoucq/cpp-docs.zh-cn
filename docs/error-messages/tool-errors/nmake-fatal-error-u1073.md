---
title: NMAKE 错误 U1073
ms.date: 11/04/2016
f1_keywords:
- U1073
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
ms.openlocfilehash: 97d44594540d18bf008757506a9e36e6d16d2cd7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182690"
---
# <a name="nmake-fatal-error-u1073"></a>NMAKE 错误 U1073

不知道如何建立 "targetname"

指定的目标不存在，并且没有要执行的命令或要应用的推理规则。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 检查目标名称的拼写。

1. 如果*targetname*为伪目标，则将其指定为另一个描述块中的目标。

1. 如果*targetname*是宏调用，请确保它不会扩展为空字符串。

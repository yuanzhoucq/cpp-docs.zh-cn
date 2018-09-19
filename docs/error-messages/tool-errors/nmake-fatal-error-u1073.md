---
title: NMAKE 错误 U1073 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1073
dev_langs:
- C++
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c309ed94cd1c984406e0d21f0139e35c6e41d7d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053930"
---
# <a name="nmake-fatal-error-u1073"></a>NMAKE 错误 U1073

不知道如何使 targetname

指定的目标不存在，并且没有要执行的命令或推理规则应用。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 检查目标名称的拼写。

1. 如果*targetname*是伪目标，指定为在另一个描述块中的目标。

1. 如果*targetname*是宏调用，一定不会扩展为空字符串。
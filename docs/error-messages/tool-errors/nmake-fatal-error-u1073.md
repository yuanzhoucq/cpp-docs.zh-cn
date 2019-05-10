---
title: NMAKE 错误 U1073
ms.date: 11/04/2016
f1_keywords:
- U1073
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
ms.openlocfilehash: 2aa02fd86906bd545373a313fa5e6e409ffb3cf9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366922"
---
# <a name="nmake-fatal-error-u1073"></a>NMAKE 错误 U1073

不知道如何使 targetname

指定的目标不存在，并且没有要执行的命令或推理规则应用。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 检查目标名称的拼写。

1. 如果*targetname*是伪目标，指定为在另一个描述块中的目标。

1. 如果*targetname*是宏调用，一定不会扩展为空字符串。
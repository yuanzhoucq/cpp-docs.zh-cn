---
title: NMAKE 错误 U1056
ms.date: 11/04/2016
f1_keywords:
- U1056
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
ms.openlocfilehash: b15b14c04dd91ae648ea4311612c122f04f90477
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367260"
---
# <a name="nmake-fatal-error-u1056"></a>NMAKE 错误 U1056

无法找到命令处理器

在中指定的路径不是命令处理器**COMSPEC**或**路径**环境变量。

NMAKE 使用 COMMAND.COM 或 cmd。作为命令处理在执行命令时的 EXE。 它会查找命令处理器首先在设置的路径**COMSPEC**。 如果**COMSPEC**不存在 NMAKE 搜索中指定的目录**路径**。
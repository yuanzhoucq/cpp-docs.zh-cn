---
title: NMAKE 错误 U1056 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1056
dev_langs:
- C++
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0a83c62bedf995708d5e99fee19f05696d05c2d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065683"
---
# <a name="nmake-fatal-error-u1056"></a>NMAKE 错误 U1056

无法找到命令处理器

在中指定的路径不是命令处理器**COMSPEC**或**路径**环境变量。

NMAKE 使用 COMMAND.COM 或 cmd。作为命令处理在执行命令时的 EXE。 它会查找命令处理器首先在设置的路径**COMSPEC**。 如果**COMSPEC**不存在 NMAKE 搜索中指定的目录**路径**。
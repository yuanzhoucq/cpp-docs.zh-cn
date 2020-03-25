---
title: NMAKE 错误 U1056
ms.date: 11/04/2016
f1_keywords:
- U1056
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
ms.openlocfilehash: 10131e518fa608292fff58672ede36390bcd665b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182898"
---
# <a name="nmake-fatal-error-u1056"></a>NMAKE 错误 U1056

无法找到命令处理器

命令处理程序不在**COMSPEC**或**path**环境变量中指定的路径中。

NMAKE 使用 COMMAND.COM 或 CMD。执行命令时，EXE 作为命令处理器。 它首先在**COMSPEC**中设置的路径中查找命令处理器。 如果**COMSPEC**不存在，NMAKE 会搜索**PATH**中指定的目录。

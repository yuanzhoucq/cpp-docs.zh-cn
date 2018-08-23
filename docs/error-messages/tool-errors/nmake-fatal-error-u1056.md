---
title: NMAKE 错误 U1056 |Microsoft 文档
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
ms.openlocfilehash: 19890e290c98fd9602d755ad35f9d47204bd6c24
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316551"
---
# <a name="nmake-fatal-error-u1056"></a>NMAKE 错误 U1056
找不到命令处理器  
  
 命令处理器未采用中指定的路径**COMSPEC**或**路径**环境变量。  
  
 NMAKE 使用 COMMAND.COM 或 cmd.为一个命令处理器执行命令时的 EXE。 它会查找命令处理器首先在设置的路径中**COMSPEC**。 如果**COMSPEC**不存在目录中指定的 NMAKE 搜索**路径**。
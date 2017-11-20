---
title: "NMAKE 错误 U1056 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1056
dev_langs: C++
helpviewer_keywords: U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d53bee02d5fe910598a87e5837678d69f03f9cf9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1056"></a>NMAKE 错误 U1056
找不到命令处理器  
  
 命令处理器未采用中指定的路径**COMSPEC**或**路径**环境变量。  
  
 NMAKE 使用 COMMAND.COM 或 cmd.为一个命令处理器执行命令时的 EXE。 它会查找命令处理器首先在设置的路径中**COMSPEC**。 如果**COMSPEC**不存在目录中指定的 NMAKE 搜索**路径**。
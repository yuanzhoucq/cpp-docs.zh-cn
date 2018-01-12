---
title: "NMAKE 错误 U1073 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1073
dev_langs: C++
helpviewer_keywords: U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: faae317df44560991a88d47ec7f123e6a8126429
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1073"></a>NMAKE 错误 U1073
不知道如何使 targetname  
  
 指定的目标不存在，并且没有要执行的命令或要应用的推理规则。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复  
  
1.  检查目标名称的拼写。  
  
2.  如果*targetname*是伪目标，它指定为另一个描述块中的目标。  
  
3.  如果*targetname*是宏调用，请确保不会扩展为空字符串。
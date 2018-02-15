---
title: .SAFESEH | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .SAFESEH
dev_langs:
- C++
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 69212e7a3542a6b6ac88ccbe2ecbbf8894862e65
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="safeseh"></a>.SAFESEH
将函数注册为结构化的异常处理程序。  
  
## <a name="syntax"></a>语法  
  
```  
  
.SAFESEH identifier  
```  
  
## <a name="remarks"></a>备注  
 *标识符*必须是本地定义的 ID [PROC](../../assembler/masm/proc.md)或[EXTRN](../../assembler/masm/extrn.md)处理器。 A[标签](../../assembler/masm/label-masm.md)不允许。 。SAFESEH 指令需要[/safeseh](../../assembler/masm/ml-and-ml64-command-line-reference.md) ml.exe 命令行选项。  
  
 有关结构化的异常处理程序的详细信息，请参阅[/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)。  
  
 例如，若要注册安全异常处理程序，创建一个新的 MASM 文件 （如下）、 与 /safeseh，组合和将其添加到所链接的对象。  
  
```  
.386  
.model  flat  
MyHandler   proto  
.safeseh    MyHandler  
end  
```  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)
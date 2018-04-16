---
title: "CL 命令文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a711b2f4a484a6370af828c5d0aad522686ca3f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cl-command-files"></a>CL 命令文件
命令文件是文本文件，其中包含选项和文件名，否则将在键入[命令行](../../build/reference/compiler-command-line-syntax.md)或指定使用[CL 环境变量](../../build/reference/cl-environment-variables.md)。 CL 接受编译器命令文件作为自变量在 CL 环境变量或命令行上。 与命令行或 CL 环境变量不同，命令文件允许使用多行选项和文件名。  
  
 命令文件名在 CL 环境变量或在命令行上的位置根据处理选项和命令文件中的文件名。 但是，如果在命令文件中会显示该 /link 选项，剩余的行上的所有选项都传递到链接器。 命令文件中的后续行中的选项和选项卡上的命令行命令文件调用后仍属编译器选项。 有关选项的顺序如何影响其解释的详细信息，请参阅[CL 选项的顺序](../../build/reference/order-of-cl-options.md)。  
  
 命令文件不能包含 CL 命令。 每个选项必须开始和结束在同一行;不能使用反斜杠 (\\) 以跨两个行合并选项。  
  
 命令文件，以指定由 at 符号 (@) 跟 filename;文件名可以指定绝对或相对路径。  
  
 例如，如果以下命令在名为响应的文件：  
  
```  
/Og /link LIBC.LIB  
```  
  
 并指定以下 CL 命令：  
  
```  
CL /Ob2 @RESP MYAPP.C  
```  
  
 到 CL 命令如下所示：  
  
```  
CL /Ob2 /Og MYAPP.C /link LIBC.LIB  
```  
  
 请注意，命令行和命令文件命令有效地组合。  
  
## <a name="see-also"></a>请参阅  
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)
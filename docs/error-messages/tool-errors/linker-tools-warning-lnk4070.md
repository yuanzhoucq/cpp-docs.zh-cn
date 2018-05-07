---
title: 链接器工具警告 LNK4070 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4070
dev_langs:
- C++
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e4599e96552f1b98ef0b1af8d38995ebbe5a83e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4070"></a>链接器工具警告 LNK4070
中的 /OUT:filename 指令。EXP 区别输出文件名 filename;忽略指令  
  
 `filename`中指定[名称](../../build/reference/name-c-cpp.md)或[库](../../build/reference/library.md)语句创建.exp 文件时区别输出`filename`，已假定默认情况下，或使用指定[/Out](../../build/reference/out-output-file-name.md)选项。  
  
 如果你更改在开发环境中和已不更新项目的.def 文件的输出文件的名称，你将看到此警告。 手动更新.def 文件以解决此警告。  
  
 使用生成的 DLL 的客户端程序可能会遇到问题。
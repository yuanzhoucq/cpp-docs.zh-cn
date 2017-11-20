---
title: "链接器工具警告 LNK4070 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4070
dev_langs: C++
helpviewer_keywords: LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ca0a31fb3512b7b11150984fc3d15013cb75c0e0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4070"></a>链接器工具警告 LNK4070
中的 /OUT:filename 指令。EXP 区别输出文件名 filename;忽略指令  
  
 `filename`中指定[名称](../../build/reference/name-c-cpp.md)或[库](../../build/reference/library.md)语句创建.exp 文件时区别输出`filename`，已假定默认情况下，或使用指定[/Out](../../build/reference/out-output-file-name.md)选项。  
  
 如果你更改在开发环境中和已不更新项目的.def 文件的输出文件的名称，你将看到此警告。 手动更新.def 文件以解决此警告。  
  
 使用生成的 DLL 的客户端程序可能会遇到问题。
---
title: "错误 C1902 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1902
dev_langs:
- C++
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: b551b1a7e0ae03a7de5108a1d114155786972847
ms.openlocfilehash: 79987719614dfa3075f9a9090ca1d97f6546ceb3
ms.lasthandoff: 02/24/2017

---
# <a name="fatal-error-c1902"></a>错误 C1902
程序数据库管理器不匹配;请检查您的安装  
  
程序数据库文件 (.pdb) 使用 mspdb 的较新版本创建*XXX*.dll 比编译器在您的系统上找到。 此错误通常指示缺少 mspdbsrv.exe 或 mspdbcore.dll 或具有不同版本与 mspdb*XXX*.dll。 ( *XXX*中 mspdb 占位符*XXX*每个产品版本的.dll 文件名称更改。 例如，在 Visual Studio 2015 中，文件名为 mspdb140.dll。）  
  
确保匹配版本的 mspdbsrv.exe、 mspdbcore.dll 和 mspdb*XXX*.dll 安装在您的系统上。 请确保版本不匹配，尚未复制到包含您的目标平台的编译器和链接工具的目录。 例如，您可能已经复制这些文件以便可以调用该编译器或链接的工具，在命令提示符下设置不**路径**环境变量相应地进行。

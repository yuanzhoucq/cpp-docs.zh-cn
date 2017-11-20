---
title: "错误 C1902 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1902
dev_langs: C++
helpviewer_keywords: C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 89354565f67c8704eee8c8b5f9dcb94523800c63
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1902"></a>错误 C1902
程序数据库管理器不匹配;请检查安装  
  
程序数据库文件 (.pdb) 使用较新版本的 mspdb 创建*XXX*比你系统上找到编译器.dll。 此错误通常表示 mspdbsrv.exe 或 mspdbcore.dll 缺少或者具有不同的版本比 mspdb*XXX*.dll。 ( *XXX*中 mspdb 占位符*XXX*随每个产品版本的.dll 文件名称更改。 例如，在 Visual Studio 2015 中，文件名为 mspdb140.dll。）  
  
确保匹配版本的 mspdbsrv.exe、 mspdbcore.dll 和 mspdb*XXX*.dll 你系统上安装。 确保不具有已不匹配的版本复制到包含目标平台的编译器和链接工具的目录。 例如，你可能具有复制文件，以便你可以调用该编译器或链接的工具，在命令提示符下设置不**路径**环境变量相应地。
---
title: "设置链接器选项 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- files [C++], LINK
- input files [C++], linker
- linker [C++], ways to set options
- linker [C++], switches
- input files [C++]
- object/library modules
ms.assetid: e08fb487-0f2e-4f24-87db-232dbc8bd2e2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b64b1dfd342598735124940d01b1bb4939242e10
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="setting-linker-options"></a>设置链接器选项
内部或外部开发环境，可以设置链接器选项。 每个链接器选项的主题讨论如何可以在开发环境中设置它。 请参阅[链接器选项](../../build/reference/linker-options.md)有关的完整列表。  
  
 在开发环境外部运行链接时，你可以指定一个或多个方面输入：  
  
-   上[命令行](../../build/reference/linker-command-line-syntax.md)  
  
-   使用[命令文件](../../build/reference/link-command-files.md)  
  
-   在[环境变量](../../build/reference/link-environment-variables.md)  
  
 链接第一个处理指定的选项在链接环境变量中，然后按照在命令行指定它们的顺序和命令文件中的选项。 如果一个选项重复使用不同的自变量，处理的最后一个优先。  
  
 选项将应用于整个生成;无选项可以应用于特定的输入文件中。  
  
## <a name="see-also"></a>另请参阅  
 [C/C++ 生成参考](../../build/reference/c-cpp-building-reference.md)   
 [链接器选项](../../build/reference/linker-options.md)
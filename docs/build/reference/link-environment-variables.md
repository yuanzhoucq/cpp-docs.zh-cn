---
title: "LINK 环境变量 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: link
dev_langs: C++
helpviewer_keywords:
- variables, environment
- LINK tool [C++], environment variables
- LIB environment variable
- environment variables [C++], LINK
ms.assetid: 9a3d3291-0cc4-4a7d-9d50-80e351b90708
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 67b36afce92140c4f205f8e5a4a46dfc7ac2d300
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="link-environment-variables"></a>LINK 环境变量

LINK 工具使用以下环境变量：  
  
-   链接和\_链接\_，如果定义。 LINK 工具预置的选项和链接环境变量中定义的自变量，并追加选项和自变量中定义\_链接\_之前处理的命令行自变量的环境变量。  
  
-   LIB（如已定义）。 LINK 工具搜索的对象、 库中或在命令行上或通过指定其他文件时使用 LIB 路径[/base](../../build/reference/base-base-address.md)选项。 它还可使用 LIB 路径查找在对象上命名的 .pdb 文件。 LIB 变量可以包含一个或多个路径规范，用分号分隔。 一个路径必须指向 Visual C++ 安装的 \lib 子目录。  
  
-   PATH，如果该工具需要运行 CVTRES 并在与 LINK 自身相同的目录中找不到文件。 （LINK 需要 CVTRES 链接 .res 文件。）PATH 必须指向 Visual C++ 安装的 \bin 子目录。  
  
-   TMP，用于链接 OMF 或.res 文件时指定目录。  
  
## <a name="see-also"></a>请参阅  

[设置链接器选项](../../build/reference/setting-linker-options.md)   
[链接器选项](../../build/reference/linker-options.md)   
[在命令行上生成 C/C++ 代码](../../build/building-on-the-command-line.md)  
[为命令行生成设置路径和环境变量](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)

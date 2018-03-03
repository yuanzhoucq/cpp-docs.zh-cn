---
title: "CL 文件名语法 |Microsoft 文档"
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
- syntax, compiler filename
- paths, CL compiler filename syntax
- cl.exe compiler, filename syntax
- extensions, specifying to compiler
- file names [C++], CL compiler
- file names [C++]
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1fc9ce614cb67bef1904e8dc464402f362b0cbde
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cl-filename-syntax"></a>CL 文件名语法
CL 接受具有遵循 FAT、HPFS 或 NTFS 命名约定的名称的文件。 任何文件名均可以包含完整或部分路径。 完整路径包括驱动器名和一个或多个目录名。 CL 接受文件名分隔通过反斜杠 (\\) 或正斜杠 （/）。 包含空格文件名必须用双引号字符引起来。 部分路径忽略 CL 假定为当前驱动器的驱动器名。 如果不指定路径，则 CL 假定该文件位于当前目录。  
  
 文件扩展名确定处理文件的方式。 已编译具有扩展名 .c、.cxx 或 .cpp 的 C 和 C++ 文件。 将其他文件（包括 .obj 文件、库 (.lib) 和模块定义 (.def) 文件）传递给链接器而无需处理。  
  
## <a name="see-also"></a>请参阅  
 [编译器命令行语法](../../build/reference/compiler-command-line-syntax.md)
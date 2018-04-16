---
title: EDITBIN 参考 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- editbin
dev_langs:
- C++
helpviewer_keywords:
- binary data, editing
- object files, modifying
- EDITBIN program
- COFF files, editing
ms.assetid: efdda03b-3dfc-4d31-90e6-caf5b3977914
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0ff9c0c58498361764dcc1b6c454c9b629d9bed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="editbin-reference"></a>EDITBIN 参考
Microsoft COFF 二进制文件编辑器 (EDITBIN。EXE) 修改通用对象文件格式 (COFF) 的二进制文件。 EDITBIN 可用于修改对象文件、 可执行文件和动态链接库 (DLL)。  
  
> [!NOTE]
>  你只能从 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 命令提示符启动此工具。 不能从系统命令提示符或从文件资源管理器启动此工具。  
  
 EDITBIN 不可用于在产生的文件上使用[/GL](../../build/reference/gl-whole-program-optimization.md)编译器选项。 对使用 /GL 生成的二进制文件进行任何修改将需要通过重新编译和链接。  
  
-   [EDITBIN 命令行](../../build/reference/editbin-command-line.md)  
  
-   [EDITBIN 选项](../../build/reference/editbin-options.md)  
  
## <a name="see-also"></a>请参阅  
 [C/C++ 生成工具](../../build/reference/c-cpp-build-tools.md)
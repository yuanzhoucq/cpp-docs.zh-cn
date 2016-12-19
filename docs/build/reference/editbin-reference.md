---
title: "EDITBIN 参考 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "editbin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "二进制数据, 编辑"
  - "COFF 文件, 编辑"
  - "EDITBIN 程序"
  - "对象文件, 修改"
ms.assetid: efdda03b-3dfc-4d31-90e6-caf5b3977914
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# EDITBIN 参考
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft COFF 二进制文件编辑器 \(EDITBIN.EXE\) 修改通用对象文件格式 \(COFF\) 二进制文件。  可以使用 EDITBIN 修改对象文件、可执行文件和动态链接库 \(DLL\)。  
  
> [!NOTE]
>  您只能从 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 命令提示符处启动此工具。  而不能从系统命令提示符或文件资源管理器中启动此工具。  
  
 EDITBIN 不可用于由 [\/GL](../../build/reference/gl-whole-program-optimization.md) 编译器选项产生的文件。  对由 \/GL 产生的二进制文件所做的任何修改必须通过重新编译和链接才能实现。  
  
-   [EDITBIN 命令行](../../build/reference/editbin-command-line.md)  
  
-   [EDITBIN 选项](../../build/reference/editbin-options.md)  
  
## 请参阅  
 [C\/C\+\+ 生成工具](../../build/reference/c-cpp-build-tools.md)
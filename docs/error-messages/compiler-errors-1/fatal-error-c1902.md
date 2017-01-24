---
title: "错误 C1902 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1902"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1902"
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1902
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

程序数据库管理器不匹配；请检查安装  
  
 创建程序数据库文件 \(.pdb\) 时所使用的 mspdb*XX*.dll 版本比编译器在您的系统上发现的版本新。  此错误通常表示缺少 mspdbsrv.exe 或 mspdbcore.dll，或者它们的版本与 mspdb*XX*dll 不同。（mspdb*XX*.dll 文件名中的 *XX*占位符会随着每个产品发行版本而更改。  例如，在 [!INCLUDE[vsprvslong](../../error-messages/compiler-errors-1/includes/vsprvslong_md.md)] 中，该文件名是 mspdb80.dll。  
  
 请确保系统上安装的 mspdbsrv.exe、mspdbcore.dll 和 mspdb*XX*.dll 的版本相匹配。  请确保未将不匹配的版本复制到包含适用于目标平台的编译器和链接工具的目录下。  例如，您可能已经复制这些文件，以便可以在命令提示处激活编译器或链接工具，而不需要相应地设置 **PATH** 环境变量。
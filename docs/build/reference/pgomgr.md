---
title: "pgomgr | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pgomgr 程序"
  - "按配置文件优化, pgomgr"
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# pgomgr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将配置文件数据从一个或多个 .pgc 文件添加到 .pgd 文件中。  
  
## 语法  
  
```  
pgomgr [options] pgcfiles pgdfile  
```  
  
#### 参数  
 `options`  
 可对 pgomgr 指定以下选项：  
  
 **\/help —** 显示可用的 pgomgr 选项（缩写为 \/?）。  
  
 **\/clear —** 清除 .pgd 文件的所有配置文件信息。  在指定了 **\/clear** 时无法指定 .pgc 文件。  
  
 **\/detail** — 显示详细统计信息，包括流图形覆盖信息。  
  
 **\/summary** — 显示每个函数的统计信息。  
  
 **\/unique** — 当与 **\/summary** 一起使用时，导致显示修饰的函数名。默认情况下，在不使用 \/unique 时，显示未修饰的函数名。  
  
 **\/merge**\[**:***n*\] — 将 .pgc 文件中的数据添加到 .pgd 文件。可选参数 *n* 用于指定数据应添加 *n* 次。例如，如果通常对方案执行 6 次，您可以用 **pgomgr \/merge:6** 使其在测试运行中执行 1 次并将它添加到 .pgd 文件中 6 次。  
  
 `pgcfiles`  
 一个或多个 .pgc 文件，需要将其配置文件数据合并到 .pgd 文件中。  可以指定单个 .pgc 文件或多个 .pgc 文件。  如果不指定任何 .pgc 文件，pgomgr 将合并与 .pgd 文件具有相同文件名的所有 .pgc 文件。  
  
 `pgdfile`  
 将来自 .pgc 文件的数据合并到其中的 .pgd 文件。  
  
## 备注  
  
> [!NOTE]
>  您只能从 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 命令提示符处启动此工具。  而不能从系统命令提示符或文件资源管理器中启动此工具。  
  
## 示例  
 在下面的示例中，清除了 .pgd 文件的配置文件数据。  
  
```  
pgomgr /clear myapp.pgd  
```  
  
 在下面的示例中，将 myapp1.pgc 中的配置文件数据添加到 .pgd 文件 3 次。  
  
```  
pgomgr /merge:3 myapp1.pgc myapp.pgd  
```  
  
 在下面的示例中，将所有 myapp\#.pgc 文件中的配置文件数据添加到 myapp.pgd 文件。  
  
```  
pgomgr -merge myapp1.pgd  
```  
  
## 请参阅  
 [用于按配置文件优化的工具](../../build/reference/tools-for-manual-profile-guided-optimization.md)
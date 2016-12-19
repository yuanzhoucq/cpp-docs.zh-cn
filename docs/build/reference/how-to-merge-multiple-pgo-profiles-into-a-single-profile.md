---
title: "如何：将多个 PGO 配置文件合并成一个配置文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "合并配置文件"
  - "按配置文件优化, 合并配置文件"
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 如何：将多个 PGO 配置文件合并成一个配置文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

配置文件引导优化 \(PGO\) 是根据已分析的方案来创建优化的二进制文件的绝好工具。  但当您的应用程序具有若干重要但又不同的方案时，该怎么办呢？如何创建单个配置文件以供 PGO 用于若干不同方案？  在 Visual Studio 中，PGO 管理器 Pgomgr.exe 将为您执行这项工作。  
  
 合并配置文件的语法是：  
  
```  
pgomgr /merge[:num] [.pgc_files] .pgd_files  
```  
  
 其中，`num` 是要用于此合并的可选权重。  如果某些方案比其他方案更重要，或者存在某些要运行多次的方案，则通常使用权重。  
  
> [!NOTE]
>  PGO 管理器将不使用陈旧的配置文件数据。  若要将 .pgc 文件合并到 .pgd 文件中，则生成 .pgc 文件的可执行文件必须由生成 .pgd 文件的同一链接调用创建。  
  
## 示例  
 在此示例中，PGO 管理器会将 pgcFile.pgc 添加到 pgdFile.pgd 中六次。  
  
```  
pgomgr /merge:6 pgcFile.pgc pgdFile.pgd  
```  
  
## 示例  
 在此示例中，PGO 管理器会将 pgcFile1.pgc 和 pgcFile2.pgc 添加到 pgdFile.pgd 中，每个 .pgc 文件添加两次。  
  
```  
pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd  
```  
  
## 示例  
 如果 PGO 管理器运行时没有 .pgc 文件，则该管理器将在本地目录中搜索所有满足下面条件的 .pgc 文件：文件名为 .pgd，其后附加有惊叹号 \(\!\)，然后紧跟任意字符。  如果本地目录中含有文件 test.pgd、test\!1.pgc、test2.pgc 和 test\!hello.pgc，并且从本地目录运行下面的命令，test\!1.pgc 和 test\!hello.pgc 将被合并到 test.pgd 中。  
  
```  
pgomgr /merge test.pgd  
```  
  
## 请参阅  
 [按配置文件优化](../../build/reference/profile-guided-optimizations.md)
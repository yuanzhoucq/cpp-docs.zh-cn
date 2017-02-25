---
title: "pgosweep | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pgosweep 程序"
  - "按配置文件优化, pgosweep"
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# pgosweep
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在按配置文件优化中用于将所有配置文件数据从正在运行的程序写入到 .pgc 文件中。  
  
## 语法  
  
```  
pgosweep [options] image pgcfile  
```  
  
#### 参数  
 `options`  
 可以留为空白的可选参数。  `options` 的有效值如下：  
  
-   **\/?** 或 **\/help,** 显示帮助消息。  
  
-   **\/noreset,** 保留运行时数据结构中的计数。  
  
 `image`  
 使用编译器选项 \/LTCG:PGINSTRUMENT 创建的 .exe 或 .dll 文件的完整路径。  
  
 `pgcfile`  
 命令将在其中写出数据计数的 .pgc 文件。  
  
## 备注  
 此命令对用 \/LTCG:PGINSTRUMENT 编译器选项生成的程序起作用。  中断正在运行的程序，并将配置文件数据写入到新的 .pgc 文件。  默认情况下，此命令将在每次写操作后重置计数。  如果指定 **\/noreset** 选项，则此命令将记录这些计数值，但在正运行的程序中不会重置它们。  如果稍后检索配置文件数据，此选项将提供副本数据。  
  
 `pgosweep` 的另一用途是仅在应用程序运行时检索配置文件信息。  例如，在启动应用程序并丢弃该文件后马上可以运行 `pgosweep`。  这将移除和启动开销相关联的配置文件数据。  然后，您在结束应用程序之前可以运行 `pgosweep`。  现在收集的数据仅具有来自运行时的配置文件信息。  
  
 命名 .pgc 文件 \(`pgcfile`\) 时，可以使用标准格式，即 *appname\!n*.pgc。  如果使用此格式，则编译器将会在 \/LTCG:PGO 阶段查找此数据。  如果没有使用标准格式，则必须使用 [pgomgr](../../build/reference/pgomgr.md) 来合并 .pgc 文件。  
  
## 示例  
  
```  
pgosweep myapp.exe myapp!1.pgc  
```  
  
 在本示例中，`pgosweep` 将 myapp.exe 的当前配置文件信息写入到 myapp\!1.pgc 中。  
  
## 请参阅  
 [用于按配置文件优化的工具](../../build/reference/tools-for-manual-profile-guided-optimization.md)
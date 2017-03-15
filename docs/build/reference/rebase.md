---
title: "/REBASE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/rebase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/REBASE editbin 选项 [C++]"
  - "基址 [C++]"
  - "DLL [C++], 链接"
  - "可执行文件 [C++], 基址"
  - "REBASE editbin 选项"
  - "-REBASE editbin 选项"
ms.assetid: 3f89d874-af5c-485b-974b-fd205f6e1a4b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /REBASE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/REBASE[:modifiers]  
```  
  
## 备注  
 此选项设置指定文件的基址。  根据四舍五入到最接近的 64 KB 的各文件大小，EDITBIN 在连续地址空间内分配新基址。  有关基址的详细信息，请参见[基址](../../build/reference/base-base-address.md) \(\/BASE\) 链接器选项。  
  
 在 EDITBIN 命令行上的 *files* 参数中，以程序的可执行文件和 DLL 的基址设置顺序指定它们。  也可以指定一个或多个 *modifiers*，每个用逗号 \(**,**\) 分隔：  
  
|修饰符|操作|  
|---------|--------|  
|BASE**\=***address*|为重新分配文件基址提供起始地址。  用十进制或 C 语言表示法指定 *address*。  如果没有指定 BASE，则默认的起始基址为 0x400000。  如果使用了 DOWN，则必须指定 BASE，*address* 设置基址范围的结束地址。|  
|BASEFILE|创建名为 COFFBASE.TXT 的文件，此文件是采用 LINK 的 \/BASE 选项所需格式的文本文件。|  
|向下键|通知 EDITBIN 从结束地址开始向下重新分配基址。  文件按指定的顺序重新分配，第一个文件位于地址范围的结束地址下面最可能的地址。  BASE 必须和 DOWN 一起使用以确保有足够的地址空间用于设置文件基址。  若要确定指定文件所需的地址空间，请在文件上运行带 \/REBASE 的 EDITBIN，并将 64 KB 添加到显示的总大小中。|  
  
## 请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)
---
title: "转储延迟加载的导入 | Microsoft Docs"
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
  - "延迟加载的导入"
  - "延迟加载的导入, 转储"
  - "导入（延迟加载）"
ms.assetid: f766acf4-9df8-4b85-8cf6-0be3ffc4c124
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 转储延迟加载的导入
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

延迟加载的导入可通过 [dumpbin \/imports](../../build/reference/imports-dumpbin.md) 转储，它显示的信息和标准导入略有不同。  它们被隔离在自已的 \/imports 转储节中，并被显式标记为延迟加载的导入。  如果映像中有卸载信息，则会注明。  如果有绑定信息，将注明目标 DLL 的时间\/日期戳连同导入的绑定地址。  
  
## 请参阅  
 [链接器的延迟加载 DLL 支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)
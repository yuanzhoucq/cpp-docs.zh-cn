---
title: "绑定导入 | Microsoft Docs"
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
  - "/DELAY:NOBIND 链接器选项"
  - "DELAY:NOBIND 链接器选项"
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 绑定导入
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

默认链接器行为是为延迟加载的 DLL 创建可绑定的导入地址表。  如果绑定了 DLL，则 Helper 函数将尝试使用绑定信息，而不是对每个引用的导入调用 **GetProcAddress**。  如果时间戳或首选地址与加载的 DLL 的时间戳或首选地址不匹配，则 Helper 函数将假设绑定导入地址表过期并将继续执行（就好像该地址表并不存在）。  
  
 如果从未打算绑定 DLL 的延迟加载导入，则在链接器的命令行上指定 [\/delay](../../build/reference/delay-delay-load-import-settings.md):nobind 将禁止生成绑定导入地址表并防止该地址表使用图像文件中的空间。  
  
## 请参阅  
 [链接器的延迟加载 DLL 支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)
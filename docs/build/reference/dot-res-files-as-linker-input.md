---
title: "用作链接器输入的 .Res 文件 | Microsoft Docs"
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
  - "用作链接器输入的 .res 文件"
  - "链接 [C++], 资源文件"
  - "RES 文件作为链接器输入"
  - "资源文件, 链接"
ms.assetid: 9c37ab00-97df-4d9a-91cd-6bf132970683
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 用作链接器输入的 .Res 文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在链接程序时，可以指定 .res 文件。  .res 文件由资源编译器 \(RC\) 创建。  LINK 自动将 .res 文件转换为 COFF。  CVTRES.exe 工具必须和 LINK.exe 在相同的目录中，或者在 PATH 环境变量中指定的目录中。  
  
## 请参阅  
 [LINK 输入文件](../../build/reference/link-input-files.md)   
 [链接器选项](../../build/reference/linker-options.md)
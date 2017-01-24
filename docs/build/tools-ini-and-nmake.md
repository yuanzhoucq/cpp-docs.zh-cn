---
title: "Tools.ini 和 NMAKE | Microsoft Docs"
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
  - "NMAKE 程序, 读取文件"
  - "Tools.ini 和 NMake"
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tools.ini 和 NMAKE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

NMAKE 在读取生成文件之前读取 Tools.ini，除非使用 \/R 选项。  它首先在当前目录中查找 Tools.ini，然后在 INIT 环境变量指定的目录中查找。  初始化文件中的 NMAKE 设置部分以 `[NMAKE]` 开头，并且可包含任何生成文件信息。  在单独一行上指定注释，以数字符号 \(\#\) 开头。  
  
## 请参阅  
 [运行 NMAKE](../build/running-nmake.md)
---
title: "路径字段限制 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_MAX_EXT"
  - "_MAX_DIR"
  - "_MAX_PATH"
  - "_MAX_FNAME"
  - "_MAX_DRIVE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_MAX_DIR 常量"
  - "_MAX_DRIVE 常量"
  - "_MAX_EXT 常量"
  - "_MAX_FNAME 常量"
  - "_MAX_PATH 常量"
  - "MAX_DIR 常量"
  - "MAX_DRIVE 常量"
  - "MAX_EXT 常量"
  - "MAX_FNAME 常量"
  - "路径字段常量"
  - "路径, 最大限制"
ms.assetid: 2b5d0e43-1347-45b4-8397-24a8a45c444e
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 路径字段限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
#include <stdlib.h>  
```  
  
## 备注  
 这些常量可以定义最大路径的长度和路径内的各个字段。  
  
|常量|含义|  
|--------|--------|  
|`_MAX_DIR`|目录组件的最大长度。|  
|`_MAX_DRIVE`|最大长度驱动器组件|  
|`_MAX_EXT`|最大长度的扩展组件|  
|`_MAX_FNAME`|最大长度文件名组成|  
|`_MAX_PATH`|最大长度完整路径|  
  
> [!NOTE]
>  C 运行时支持路径长度。长度为 32768，但由操作系统，尤其是文件系统，支持这些较长的路径。  字段的总和不应超过的完全向后兼容的 `_MAX_PATH` 使用 FAT32 文件系统。  [!INCLUDE[win2kfamily](../c-runtime-library/includes/win2kfamily_md.md)]、[!INCLUDE[WinXpFamily](../c-runtime-library/includes/winxpfamily_md.md)]、[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]和 Windows Vista 支持 NTFS 文件系统路径。长度为 32768，不过，只有使用 Unicode 时 API。  当使用长的路径名时，将路径添加前缀字符\\\\?\\ and use the Unicode versions of the C Runtime 函数。  
  
## 请参阅  
 [全局常量](../c-runtime-library/global-constants.md)
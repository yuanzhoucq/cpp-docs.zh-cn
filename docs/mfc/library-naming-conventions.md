---
title: "库命名约定 | Microsoft Docs"
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
  - "编码约定, MFC 库名"
  - "控制台应用程序, MFC 库版本"
  - "约定 [C++], MFC 库名"
  - "库 [C++], static"
  - "MFC 库, 命名规则"
  - "NAFXCW.LIB"
  - "NAFXCWD.LIB"
  - "命名规则 [C++], MFC 对象代码库"
  - "对象代码库"
  - "对象代码库, MFC 命名约定"
ms.assetid: 39fe7d93-5a14-4c6a-b16c-bf318fa01278
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 库命名约定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 对象的库代码使用以下命名约定。  在其中窗体库名  
  
 *u*AFX`c`W`d`.LIB  
  
 在斜体在小写字母显示的含义。下表显示" specifier 的占位符：  
  
### 库命名约定  
  
|说明符|值和意义|  
|---------|----------|  
|*u*|ANSI \(n\) 或 Unicode \(u\)|  
|`c`|创建的程序类型：C\=all|  
|`d`|调试或发布：D\=Debug;忽略版本的说明符|  
  
 默认是生成应用 Intel 平台的"调试 Windows ANSI 应用程序：NAFXCWD.Lib.  下表列出的所有库是在\\atlmfc\\lib directory on the Visual C\+\+ CD\-ROM 中包括预生成的。  
  
### 静态链接库命名约定  
  
|库|说明|  
|-------|--------|  
|NAFXCW.LIB|MFC 静态链接库 \(DLL\)，发布版本|  
|NAFXCWD.LIB|MFC 静态链接库 \(DLL\)，调试版本|  
|UAFXCW.LIB|具有 Unicode 支持的 MFC 发布静态链接库版本，|  
|NAFXCWD.LIB|具有 Unicode 支持的 MFC 编译静态链接库版本，|  
  
> [!NOTE]
>  如果需要生成库版本，请参见在\\ atlmfc \\ \\ mfc src 目录的 Readme.Txt 文件。  此文件描述用于 NMAKE 中提供的生成文件。  
  
 有关更多信息，请参见 [MFC 的 DLL 命名约定](../build/naming-conventions-for-mfc-dlls.md) 和 [MFC 库的 Unicode 版本](../mfc/unicode-in-mfc.md)。  
  
## 请参阅  
 [MFC 库版本](../mfc/mfc-library-versions.md)
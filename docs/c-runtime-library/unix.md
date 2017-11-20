---
title: UNIX | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: unix
dev_langs: C++
helpviewer_keywords:
- UNIX
- POSIX compatibility
- POSIX file names
- UNIX, compatibility
ms.assetid: 40792414-7a5b-415d-bfa8-2bfb1ebb3731
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8db5466439b72c4291383913451bcf5a0b415848
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="unix"></a>UNIX
如果您计划将程序移植到 UNIX，请遵循以下准则：  
  
-   不要从 SYS 子目录中移除标头文件。 仅当您不打算将程序传输到 UNIX 时，可以将 SYS 标头文件放置到其他位置。  
  
-   在采用将路径和文件名表示为参数的字符串的例程中使用与 UNIX 兼容的路径分隔符。 为此，UNIX 仅支持正斜杠 (/)，而 Win32 操作系统同时支持反斜杠 (\\) 和正斜杠 (/)。 因此，本文档将与 UNIX 兼容的正斜杠用作路径分隔符，例如在 `#include` 语句中。 （但是，Windows 操作系统命令外壳 (CMD.EXE) 不支持在从命令提示符处输入的命令中使用正斜杠。）  
  
-   使用在 UNIX 中正常运行的路径和文件名（区分大小写）。 Win32 操作系统中的文件分配表 (FAT) 文件系统不区分大小写；NTFS 文件系统保留目录列表的大小写形式，但在文件搜索和其他系统操作中将忽略大小写。  
  
    > [!NOTE]
    >  在此版本的 Visual C++ 中，已从函数描述中删除 UNIX 兼容性信息。  
  
## <a name="see-also"></a>另请参阅  
 [兼容性](../c-runtime-library/compatibility.md)
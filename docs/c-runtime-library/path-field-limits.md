---
title: "路径字段限制 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _MAX_EXT
- _MAX_DIR
- _MAX_PATH
- _MAX_FNAME
- _MAX_DRIVE
dev_langs:
- C++
helpviewer_keywords:
- path field constants
- MAX_FNAME constant
- _MAX_DIR constant
- _MAX_DRIVE constant
- paths, maximum limit
- _MAX_PATH constant
- MAX_DRIVE constant
- _MAX_FNAME constant
- _MAX_EXT constant
- MAX_DIR constant
- MAX_EXT constant
ms.assetid: 2b5d0e43-1347-45b4-8397-24a8a45c444e
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 0adde41ca70fa5fdc457772f6023b02f9550e2ca
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="path-field-limits"></a>路径字段限制
## <a name="syntax"></a>语法  
  
```  
#include <stdlib.h>  
```  
  
## <a name="remarks"></a>备注  
 这些常量定义路径的最大长度以及路径内的单个字段的最大长度。  
  
|常量|含义|  
|--------------|-------------|  
|`_MAX_DIR`|目录组件的最大长度|  
|`_MAX_DRIVE`|驱动器组件的最大长度|  
|`_MAX_EXT`|扩展组件的最大长度|  
|`_MAX_FNAME`|文件名组件的最大长度|  
|`_MAX_PATH`|完整路径的最大长度|  
  
> [!NOTE]
>  C 运行库支持的路径的最大长度为 32768 个字符，但这取决于操作系统（特别是文件系统）支持这些较长的路径。 字段长度的总和不应超过 `_MAX_PATH` 以便与 FAT32 文件系统完全向后兼容。 [!INCLUDE[win2kfamily](../c-runtime-library/includes/win2kfamily_md.md)]、[!INCLUDE[WinXpFamily](../atl/reference/includes/winxpfamily_md.md)]、[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 和 Windows Vista NTFS 文件系统支持的路径的最大长度为 32768 个字符（但仅在使用 Unicode API 时才支持）。 在使用较长的路径名时，为路径添加字符 \\\\?\ 作为前缀，并使用 Unicode 版本的 C 运行时函数。  
  
## <a name="see-also"></a>另请参阅  
 [全局常量](../c-runtime-library/global-constants.md)

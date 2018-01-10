---
title: "文件权限常量 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _S_IWRITE
- _S_IREAD
dev_langs: C++
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 123b5f14c6d13e7ee7ff41de00816234d6e45fc8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="file-permission-constants"></a>文件权限常量
## <a name="syntax"></a>语法  
  
```  
  
#include <sys/stat.h>  
  
```  
  
## <a name="remarks"></a>备注  
 当指定 `_O_CREAT`（`_open` 或 `_sopen`）时需要这些常量中的一个。  
  
 `pmode` 参数按以下方式指定文件的权限设置。  
  
|返回的常量|含义|  
|--------------|-------------|  
|`_S_IREAD`|允许读取|  
|`_S_IWRITE`|允许写入|  
|`_S_IREAD` &#124; `_S_IWRITE`|允许读取和写入。|  
  
 当用作 `pmode` 的 `_umask` 参数时，清单常量将设置权限设置，如下所示。  
  
|返回的常量|含义|  
|--------------|-------------|  
|`_S_IREAD`|不允许写入（文件是只读的）|  
|`_S_IWRITE`|不允许读取（文件是只写的）|  
|`_S_IREAD` &#124; `_S_IWRITE`|既不允许读取也不允许写入|  
  
## <a name="see-also"></a>请参阅  
 [_open、_wopen](../c-runtime-library/reference/open-wopen.md)   
 [_sopen、_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [_umask](../c-runtime-library/reference/umask.md)   
 [标准类型](../c-runtime-library/standard-types.md)   
 [全局常量](../c-runtime-library/global-constants.md)
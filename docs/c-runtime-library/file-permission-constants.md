---
title: "文件权限常量 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _S_IWRITE
- _S_IREAD
dev_langs:
- C++
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: fe25cc1ce973d46c87425b59cc2da3544b216033
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="file-permission-constants"></a>文件权限常量
## <a name="syntax"></a>语法  
  
```  
  
#include <sys/stat.h>  
  
```  
  
## <a name="remarks"></a>备注  
 当指定 `_O_CREAT`（`_open` 或 `_sopen`）时需要这些常量中的一个。  
  
 `pmode` 参数按以下方式指定文件的权限设置。  
  
|常量|含义|  
|--------------|-------------|  
|`_S_IREAD`|允许读取|  
|`_S_IWRITE`|允许写入|  
|`_S_IREAD` &#124; `_S_IWRITE`|允许读取和写入。|  
  
 当用作 `pmode` 的 `_umask` 参数时，清单常量将设置权限设置，如下所示。  
  
|常量|含义|  
|--------------|-------------|  
|`_S_IREAD`|不允许写入（文件是只读的）|  
|`_S_IWRITE`|不允许读取（文件是只写的）|  
|`_S_IREAD` &#124; `_S_IWRITE`|既不允许读取也不允许写入|  
  
## <a name="see-also"></a>另请参阅  
 [_open、_wopen](../c-runtime-library/reference/open-wopen.md)   
 [_sopen、_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [_umask](../c-runtime-library/reference/umask.md)   
 [标准类型](../c-runtime-library/standard-types.md)   
 [全局常量](../c-runtime-library/global-constants.md)

---
title: "_stat 结构 st_mode 字段常量 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- S_IFCHR
- S_IFDIR
- _S_IWRITE
- S_IFMT
- _S_IFDIR
- _S_IREAD
- S_IEXEC
- _S_IEXEC
- _S_IFMT
- S_IWRITE
- S_IFREG
- S_IREAD
- _S_IFCHR
- _S_IFREG
dev_langs:
- C++
helpviewer_keywords:
- S_IFDIR constant
- stat structure
- S_IWRITE constant
- S_IEXEC constant
- _S_IFREG constant
- S_IREAD constant
- stat structure, constants
- _S_IFMT constant
- st_mode field constants
- S_IFMT constant
- _S_IEXEC constant
- _S_IWRITE constant
- _S_IFDIR constant
- S_IFREG constant
- S_IFCHR constant
- _S_IREAD constant
- _S_IFCHR constant
ms.assetid: fd462004-7563-4766-8443-30b0a86174b6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6d5502a563c674818626627a5161e7051682f258
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="stat-structure-stmode-field-constants"></a>_stat 结构 st_mode 字段常量
## <a name="syntax"></a>语法  
  
```  
  
#include <sys/stat.h>  
  
```  
  
## <a name="remarks"></a>备注  
 这些常量用于指示 [_stat 结构](../c-runtime-library/standard-types.md)的 **st_mode** 字段中的文件类型。  
  
 下面描述了位掩码常量：  
  
|返回的常量|含义|  
|--------------|-------------|  
|`_S_IFMT`|文件类型掩码|  
|`_S_IFDIR`|目录|  
|`_S_IFCHR`|特殊字符（指示设备，如果已设置）|  
|`_S_IFREG`|规则|  
|`_S_IREAD`|读取权限，所有者|  
|`_S_IWRITE`|写入权限，所有者|  
|`_S_IEXEC`|执行/搜索权限，所有者|  
  
## <a name="see-also"></a>请参阅  
 [_stat、_wstat 函数](../c-runtime-library/reference/stat-functions.md)   
 [_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [标准类型](../c-runtime-library/standard-types.md)   
 [全局常量](../c-runtime-library/global-constants.md)
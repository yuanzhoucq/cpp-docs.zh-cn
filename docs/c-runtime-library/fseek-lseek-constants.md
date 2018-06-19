---
title: fseek、_lseek 常量 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- SEEK_END
- SEEK_SET
- SEEK_CUR
dev_langs:
- C++
helpviewer_keywords:
- SEEK_SET constant
- SEEK_END constant
- SEEK_CUR constant
ms.assetid: 9deeb13e-5aa3-4c33-80d8-721c80a4de9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fbcf0a1106610740a585b7e4f8b68e3fc9b6a8f7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388443"
---
# <a name="fseek-lseek-constants"></a>fseek、_lseek 常量
## <a name="syntax"></a>语法  
  
```  
  
#include <stdio.h>  
  
```  
  
## <a name="remarks"></a>备注  
 origin 参数指定初始位置，可以是下列清单常量之一：  
  
|返回的常量|含义|  
|--------------|-------------|  
|`SEEK_END`|文件结尾|  
|`SEEK_CUR`|文件指针的当前位置|  
|`SEEK_SET`|文件开头|  
  
## <a name="see-also"></a>请参阅  
 [fseek、_fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)   
 [_lseek、_lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)   
 [全局常量](../c-runtime-library/global-constants.md)
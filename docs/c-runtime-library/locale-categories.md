---
title: 区域设置类别 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- LC_MAX
- LC_MIN
- LC_MONETARY
- LC_TIME
- LC_NUMERIC
- LC_COLLATE
- LC_CTYPE
- LC_ALL
dev_langs:
- C++
helpviewer_keywords:
- LC_MIN constant
- LC_MONETARY constant
- LC_CTYPE constant
- locale constants
- LC_MAX constant
- LC_ALL constant
- LC_TIME constant
- LC_NUMERIC constant
- LC_COLLATE constant
ms.assetid: 868f1493-fe5d-4722-acab-bfcd374a063a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5087fd42a5fd1c104d8587091996e58f78442b1e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="locale-categories"></a>区域设置类别
## <a name="syntax"></a>语法  
  
```  
  
#include <locale.h>  
  
```  
  
## <a name="remarks"></a>备注  
 区域设置类别是本地化例程使用的清单常量，用于指定要使用的程序区域设置信息部分。 区域设置是指可为其自定义程序的某些方面的局部性（或国家/地区）。 与区域设置相关的部分包括日期的格式设置和货币值的显示格式等。  
  
|区域设置类别|影响的程序部分|  
|---------------------|-------------------------------|  
|`LC_ALL`|所有区域设置特定的行为（所有类别）|  
|`LC_COLLATE`|`strcoll` 和 `strxfrm` 函数的行为|  
|`LC_CTYPE`|字符处理函数的行为（不受影响的 isdigit、`isxdigit`、`mbstowcs` 和 `mbtowc` 除外）|  
|`LC_MAX`|与 `LC_TIME` 相同|  
|`LC_MIN`|与 `LC_ALL` 相同|  
|`LC_MONETARY`|`localeconv` 函数返回的货币格式信息|  
|`LC_NUMERIC`|格式化输出例程（例如 `printf`）、数据转换例程和 `localeconv` 函数所返回的非货币格式设置信息的小数点字符|  
|`LC_TIME`|`strftime` 函数的行为|  
  
 有关示例，请参阅 [setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。  
  
## <a name="see-also"></a>请参阅  
 [localeconv](../c-runtime-library/reference/localeconv.md)   
 [setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll 函数](../c-runtime-library/strcoll-functions.md)   
 [strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)   
 [全局常量](../c-runtime-library/global-constants.md)
---
title: "_get_timezone | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _get_timezone
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_timezone
- get_timezone
dev_langs:
- C++
helpviewer_keywords:
- time zones
- get_timezone function
- _get_timezone function
ms.assetid: 30ab0838-0ae9-4a2f-bfe6-a49ee443b21e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3ee251c147fd0f3f34d229cafbbef28caf1cebd9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="gettimezone"></a>_get_timezone
检索协调世界时 (UTC) 和当地时间之间的差异（以秒为单位）。  
  
## <a name="syntax"></a>语法  
  
```  
  
      error_t _get_timezone(   
    long* seconds  
);  
```  
  
#### <a name="parameters"></a>参数  
 `seconds`  
 UTC 和当地时间之间的差异（以秒为单位）。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为零；如果发生错误，则为 `errno` 值。  
  
## <a name="remarks"></a>备注  
 `_get_timezone` 函数检索 UTC 与当地时间之间的差异（以秒为单位表示的整数）。 对于太平洋标准时间（比 UTC 时间晚 8 个小时），默认值是 28,800 秒。  
  
 如果 `seconds` 为 `NULL`，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_get_timezone`|\<time.h>|  
  
 有关详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)   
 [_get_daylight](../../c-runtime-library/reference/get-daylight.md)   
 [_get_dstbias](../../c-runtime-library/reference/get-dstbias.md)   
 [_get_tzname](../../c-runtime-library/reference/get-tzname.md)
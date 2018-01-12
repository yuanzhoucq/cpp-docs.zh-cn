---
title: "_get_tzname | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_tzname
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
- _get_tzname
- get_tzname
dev_langs: C++
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3f70e928c3877bf5d660231cbe2646f6cf72575e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="gettzname"></a>_get_tzname
检索时区名称或夏令时标准时区名称 (DST) 的字符串表示形式。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t _get_tzname(  
    size_t* pReturnValue,  
    char* timeZoneName,  
    size_t sizeInBytes,  
    int index      
);  
```  
  
#### <a name="parameters"></a>参数  
 [out] `pReturnValue`  
 包括 NULL 终止符的 `timeZoneName` 的字符串长度。  
  
 [out] `timeZoneName`  
 具体取决于 `index` 的时区名称或夏令时标准时区名称 (DST) 表示形式的字符串的地址。  
  
 [in] `sizeInBytes`  
 `timeZoneName` 字符串的大小，以字节为单位。  
  
 [in] `index`  
 要检索的两个时区名称之一的索引。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为零；否则为 `errno` 类型值。  
  
 如果 `timeZoneName` 为 `NULL`，或 `sizeInBytes` 为零或小于零（但不同时满足以上两个条件），则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。  
  
### <a name="error-conditions"></a>错误条件  
  
|`pReturnValue`|`timeZoneName`|`sizeInBytes`|`index`|返回值|`timeZoneName` 的内容|  
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|  
|TZ 名称的大小|`NULL`|0|0 或 1|0|未修改|  
|TZ 名称的大小|任何|> 0|0 或 1|0|TZ 名称|  
|未修改|`NULL`|> 0|任何|`EINVAL`|未修改|  
|未修改|任何|零|任何|`EINVAL`|未修改|  
|未修改|任何|> 0|> 1|`EINVAL`|未修改|  
  
## <a name="remarks"></a>备注  
 `_get_tzname` 函数根据索引值检索 `timeZoneName` 地址中的时区名称或夏令时标准时区名称 (DST) 的字符串表示形式，并检索 `pReturnValue` 中字符串的大小。 如果 `timeZoneName` 为 `NULL` 且 `sizeInBytes` 为零，`pReturnValue` 中仅返回任一时区的字符串大小（以字节为单位）。 标准时区的索引值必须为 0，夏令时标准时区的索引值必须为 1；索引的任何其他值都具有不确定的结果。  
  
### <a name="index-values"></a>索引值  
  
|`index`|`timeZoneName` 的内容|`timeZoneName` 默认值|  
|-------------|--------------------------------|----------------------------------|  
|0|时区名称|"PST"|  
|1|夏令时标准时区名称|"PDT"|  
|> 1 或 < 0|将 `errno` 设置为 `EINVAL`|未修改|  
  
 除非在运行时显式更改值，默认值分别为 "PST" 和 "PDT"。  这些字符数组的大小由 `TZNAME_MAX` 值控制。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_get_tzname`|\<time.h>|  
  
 有关详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)   
 [_get_daylight](../../c-runtime-library/reference/get-daylight.md)   
 [_get_dstbias](../../c-runtime-library/reference/get-dstbias.md)   
 [_get_timezone](../../c-runtime-library/reference/get-timezone.md)   
 [TZNAME_MAX](../../c-runtime-library/tzname-max.md)
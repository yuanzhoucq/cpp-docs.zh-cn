---
title: "_set_doserrno | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_doserrno
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_doserrno
- set_doserrno
dev_langs: C++
helpviewer_keywords:
- _set_doserrno function
- doserrno global variable
- set_doserrno function
- _doserrno global variable
ms.assetid: 8686c159-3797-4705-a53e-7457869ca6f3
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f2105c6e3479b1d46e5f61687878190870a0e10e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="setdoserrno"></a>_set_doserrno
设置 [_doserrno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 全局变量的值。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t _set_doserrno(   
   int value   
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `value`  
 `_doserrno` 的新值。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 0。  
  
## <a name="remarks"></a>备注  
 可能的值是在 Errno.h 中定义的。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|可选标头|  
|-------------|---------------------|---------------------|  
|`_set_doserrno`|\<stdlib.h>|\<errno.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>请参阅  
 [_get_doserrno](../../c-runtime-library/reference/get-doserrno.md)   
 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)
---
title: "_rmtmp | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _rmtmp
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- rmtmp
- _rmtmp
dev_langs: C++
helpviewer_keywords:
- removing temporary files
- _rmtmp function
- files [C++], temporary
- rmtmp function
- files [C++], removing
- temporary files [C++], removing
ms.assetid: 7419501e-2587-4f2a-b469-0dca07f84736
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 12a0bef6622d8f65b450701dcfb86976da6029da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="rmtmp"></a>_rmtmp
删除临时文件。  
  
## <a name="syntax"></a>语法  
  
```  
  
int _rmtmp( void );  
```  
  
## <a name="return-value"></a>返回值  
 `_rmtmp` 将返回已关闭和删除的临时文件的数量。  
  
## <a name="remarks"></a>备注  
 `_rmtmp` 函数将清除当前目录中的所有临时文件。 该函数将仅删除由 `tmpfile` 创建的那些文件；应仅在创建临时文件的相同目录下使用该函数。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_rmtmp`|\<stdio.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
 请参阅 [tmpfile](../../c-runtime-library/reference/tmpfile.md) 的示例。  
  
## <a name="see-also"></a>请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [_flushall](../../c-runtime-library/reference/flushall.md)   
 [tmpfile](../../c-runtime-library/reference/tmpfile.md)   
 [_tempnam、_wtempnam、tmpnam、_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)
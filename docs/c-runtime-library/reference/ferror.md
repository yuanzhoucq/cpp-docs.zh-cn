---
title: "ferror | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ferror
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
- ferror
dev_langs:
- C++
helpviewer_keywords:
- ferror function
- streams, testing for errors
- errors [C++], testing for stream
ms.assetid: 528a34bc-f2aa-4c3f-b89a-5b148e6864f7
caps.latest.revision: 13
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 61ceb0f31f41e129eb0047ba8c0de1c44c43f1b1
ms.lasthandoff: 02/24/2017

---
# <a name="ferror"></a>ferror
测试流中的错误。  
  
## <a name="syntax"></a>语法  
  
```  
int ferror(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## <a name="return-value"></a>返回值  
 如果 `stream` 中未发生错误，则 `ferror` 将返回 0。 否则，返回一个非零值。 如果流为 `NULL`， `ferror` 将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回 0。  
  
 有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `ferror` 例程（同时作为函数和宏实现）测试与 `stream` 相关联的文件的读取或写入错误。 如果发生错误，则流的错误指示符将保留设置，直到关闭或回退流，或直到针对流调用 `clearerr`。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`ferror`|\<stdio.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 请参阅 [feof](../../c-runtime-library/reference/feof.md) 的示例。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [错误处理](../../c-runtime-library/error-handling-crt.md)   
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [_eof](../../c-runtime-library/reference/eof.md)   
 [feof](../../c-runtime-library/reference/feof.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [perror、_wperror](../../c-runtime-library/reference/perror-wperror.md)

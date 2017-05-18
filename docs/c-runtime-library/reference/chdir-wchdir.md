---
title: "_chdir、_wchdir | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wchdir
- _chdir
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- tchdir
- _chdir
- _wchdir
- _tchdir
- wchdir
dev_langs:
- C++
helpviewer_keywords:
- _tchdir function
- _chdir function
- _wchdir function
- tchdir function
- wchdir function
- chdir function
- directories [C++], changing
ms.assetid: 85e9393b-62ac-45d5-ab2a-fa2217f6152e
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 14d6eb678a20d3f3fb0a6250e13005d904aed4b1
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="chdir-wchdir"></a>_chdir、_wchdir
更改当前工作目录。  
  
## <a name="syntax"></a>语法  
  
```  
int _chdir(   
   const char *dirname   
);  
int _wchdir(   
   const wchar_t *dirname   
);  
```  
  
#### <a name="parameters"></a>参数  
 `dirname`  
 新工作目录的路径。  
  
## <a name="return-value"></a>返回值  
 如果成功，这些函数会返回值 0。 返回值-1 表示失败。 如果找不到指定路径，则 `errno` 设置为 `ENOENT`。 如果 `dirname` 为 NULL，则会调用无效的参数处理程序，如 [Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允许继续执行，则将 `errno` 设置为 `EINVAL` 并且该函数将返回 -1。  
  
## <a name="remarks"></a>备注  
 `_chdir` 函数将当前工作目录更改为 `dirname`指定的目录。 `dirname` 参数必须引用现有目录。 此函数可更改任何驱动器上的当前工作目录。 如果在 `dirname`中指定了新的驱动器号，则也会更改默认的驱动器号。 例如，如果 A 为默认的驱动器号而 \BIN 是当前工作目录，则以下调用会更改驱动器 C 的当前工作目录，且会将 C 建立为新的默认驱动器：  
  
```  
_chdir("c:\\temp");  
```  
  
 但你在路径中使用可选的反斜杠字符 (`\`) 时，必须在 C 字符串中放置两个反斜杠 (`\\`)，以表示单个反斜杠 (`\`)。  
  
 `_wchdir` 是 `_chdir`的宽字符版本； `dirname` 的 `_wchdir` 参数是宽字符字符串，但是`. _wchdir` 和 `_chdir` 的行为相同。  
  
### <a name="generic-text-routine-mapping"></a>一般文本例程映射：  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tchdir`|`_chdir`|`_chdir`|`_wchdir`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|---------------------|  
|`_chdir`|\<direct.h>|\<errno.h>|  
|`_wchdir`|\<direct.h> 或 \<wchar.h>|\<errno.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_chdir.c  
// arguments: C:\WINDOWS  
  
/* This program uses the _chdir function to verify  
   that a given directory exists. */  
  
#include <direct.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main( int argc, char *argv[] )  
{  
  
   if(_chdir( argv[1] ) )  
   {  
      switch (errno)  
      {  
      case ENOENT:  
         printf( "Unable to locate the directory: %s\n", argv[1] );  
         break;  
      case EINVAL:  
         printf( "Invalid buffer.\n");  
         break;  
      default:  
         printf( "Unknown error.\n");  
      }  
   }  
   else  
      system( "dir *.exe");  
}  
```  
  
```Output  
Volume in drive C has no label.  
 Volume Serial Number is 2018-08A1  
  
 Directory of c:\windows  
  
08/29/2002  04:00 AM         1,004,032 explorer.exe  
12/17/2002  04:43 PM            10,752 hh.exe  
03/03/2003  09:24 AM            33,792 ieuninst.exe  
10/29/1998  04:45 PM           306,688 IsUninst.exe  
08/29/2002  04:00 AM            66,048 NOTEPAD.EXE  
03/03/2003  09:24 AM            33,792 Q330994.exe  
08/29/2002  04:00 AM           134,144 regedit.exe  
02/28/2003  06:26 PM            46,352 setdebug.exe  
08/29/2002  04:00 AM            15,360 TASKMAN.EXE  
08/29/2002  04:00 AM            49,680 twunk_16.exe  
08/29/2002  04:00 AM            25,600 twunk_32.exe  
08/29/2002  04:00 AM           256,192 winhelp.exe  
08/29/2002  04:00 AM           266,752 winhlp32.exe  
              13 File(s)      2,249,184 bytes  
               0 Dir(s)  67,326,029,824 bytes free  
```  
  
## <a name="see-also"></a>另请参阅  
 [目录控制](../../c-runtime-library/directory-control.md)   
 [_mkdir、_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [_rmdir、_wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)   
 [system、_wsystem](../../c-runtime-library/reference/system-wsystem.md)

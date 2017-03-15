---
title: "_getdrives | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getdrives
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
- getdrives
- _getdrives
dev_langs:
- C++
helpviewer_keywords:
- _getdrives function
- getdrives function
- disk drives
ms.assetid: 869bb51f-4209-4328-846e-3aadebaceb9c
caps.latest.revision: 18
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
ms.openlocfilehash: b8052d82a223402849b6ba48ce5f6621a7d27ed9
ms.lasthandoff: 02/24/2017

---
# <a name="getdrives"></a>_getdrives
返回一个表示当前可用的磁盘驱动器的位掩码。  
  
> [!IMPORTANT]
>  此 API 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned long _getdrives( void );  
```  
  
## <a name="return-value"></a>返回值  
 如果函数成功，则返回值是一个表示当前可用的磁盘驱动器的位掩码。 位位置 0（最低有效位）是驱动器 A，位位置 1 是驱动器 B，位位置 2 是驱动器 C，依此类推。 如果函数失败，则返回值为零。 若要获得扩展的错误信息，请调用 `GetLastError`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_getdrives`|\<direct.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
  
      // crt_getdrives.c  
// This program retrives and lists out  
// all the logical drives that are   
// currently mounted on the machine.  
  
#include <windows.h>  
#include <direct.h>  
#include <stdio.h>  
#include <tchar.h>  
  
TCHAR g_szDrvMsg[] = _T("A:\n");  
  
int main(int argc, char* argv[]) {  
   ULONG uDriveMask = _getdrives();  
  
   if (uDriveMask == 0)  
   {  
      printf( "_getdrives() failed with failure code: %d\n",  
              GetLastError());  
   }  
   else  
   {  
      printf("The following logical drives are being used:\n");  
  
      while (uDriveMask) {  
         if (uDriveMask & 1)  
            printf(g_szDrvMsg);  
  
         ++g_szDrvMsg[0];  
         uDriveMask >>= 1;  
      }  
   }  
}  
```  
  
```Output  
The following logical drives are being used:  
A:  
C:  
D:  
E:  
```  
  
## <a name="net-framework-equivalent"></a>NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [目录控制](../../c-runtime-library/directory-control.md)

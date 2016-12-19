---
title: "_getdrives | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_getdrives"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "getdrives"
  - "_getdrives"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getdrives 函数"
  - "磁盘驱动器"
  - "getdrives 函数"
ms.assetid: 869bb51f-4209-4328-846e-3aadebaceb9c
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _getdrives
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回一个表示当前可用的磁盘驱动器的位掩码。  
  
> [!IMPORTANT]
>  此 API 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。  有关详细信息，请参阅 [\/ZW 不支持 CRT 函数](http://msdn.microsoft.com/ZH-CN/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
unsigned long _getdrives( void );  
```  
  
## 返回值  
 如果函数成功，则返回值是一个表示当前可用的磁盘驱动器的位掩码。  位位置 0（最低有效位）是驱动器 A，位位置 1 是驱动器 B，位位置 2 是驱动器 C，依此类推。  如果函数失败，则返回值为零。  若要获得扩展的错误信息，请调用 `GetLastError`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_getdrives`|\<direct.h\>|  
  
 有关更多兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
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
  
  **The following logical drives are being used:**  
**A：**  
**C:**  
**D:**  
**E:**   
## NET Framework 等效项  
 不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [目录控制](../../c-runtime-library/directory-control.md)
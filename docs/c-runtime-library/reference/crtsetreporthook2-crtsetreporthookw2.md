---
title: "_CrtSetReportHook2、_CrtSetReportHookW2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtSetReportHook2"
  - "_CrtSetReportHookW2"
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
apitype: "DLLExport"
f1_keywords: 
  - "CrtSetReportHookW2"
  - "CrtSetReportHook2"
  - "_CrtSetReportHookW2"
  - "_CrtSetReportHook2"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CrtSetReportHook2 函数"
  - "_CrtSetReportHook2 函数"
  - "_CrtSetReportHookW2 函数"
  - "CrtSetReportHookW2 函数"
ms.assetid: 12e5f68d-c8a7-4b1a-9a75-72ba4a8592d0
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _CrtSetReportHook2、_CrtSetReportHookW2
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过挂接到C运行时调试申报程序（仅调试版本）来安装或卸载一个客户端自定义报告函数。  
  
## 语法  
  
```  
  
      int _CrtSetReportHook2(  
   int mode,  
   _CRT_REPORT_HOOK pfnNewHook  
);  
int _CrtSetReportHookW2(  
   int mode,  
   _CRT_REPORT_HOOKW pfnNewHook  
);  
```  
  
#### 参数  
 `mode`  
 要执行的操作: `_CRT_RPTHOOK_INSTALL` or `_CRT_RPTHOOK_REMOVE`。  
  
 `pfnNewHook`  
 报告挂钩安装或移除此函数以减少字符版本。  
  
 `pfnNewHook`  
 报告挂钩安装或移除此函数以减少字符版本。  
  
## 返回值  
 \-1，如果遇到错误，则与 `EINVAL` 或 `ENOMEM` 设置；则在调用之后返回 `pfnNewHook` 引用计数。  
  
## 备注  
 `_CrtSetReportHook2` 和 `_CrtSetReportHookW2` 可以挂钩或解除挂钩函数，即，而仅可以挂钩函数。[\_CrtSetReportHook](../../c-runtime-library/reference/crtsetreporthook.md)  
  
 应使用`_CrtSetReportHook2` 或 `_CrtSetReportHookW2` 替代 `_CrtSetReportHook`，则挂钩调用 DLL 中时调用，并且，当多个 DLL 可能是加载并将其挂钩函数。  在这种情况下 DLL，以不同顺序与其加载的可卸载，并可以挂钩函数保留点已卸载的 DLL。  如果挂钩函数 `_CrtSetReportHook`，添加了与任何输出调试崩溃进程。  
  
 所有与挂钩函数将调用 `_CrtSetReportHook`，如果未挂钩函数添加带有 `_CrtSetReportHook2` 或 `_CrtSetReportHookW2` 或者，如果挂钩函数将所有具有 `_CrtSetReportHook2` 和 `_CrtSetReportHookW2` 返回 `FALSE`。  
  
 此函数宽字符版本可用。  报告挂钩函数执行类型的字符串 \(宽或缩小的字符\) 必须与使用的此函数版本。  对于报告挂钩使用下列函数原型用于此函数宽字符版本：  
  
```  
int YourReportHook( int reportType, wchar_t *message, int *returnValue );  
```  
  
 对于窄字符使用报告挂钩以下原型：  
  
```  
int YourReportHook( int reportType, char *message, int *returnValue );  
```  
  
 这些函数验证其参数。  如果 `mode`或`pfnNewNook`是[参数验证](../../c-runtime-library/parameter-validation.md), 则函数调用无效参数处理程序, 如所述.  如果允许执行继续，则这些功能将 `EINVAL` 设置为 `errno` 并返回 \-1。  
  
> [!NOTE]
>  如果你的应用程序使用 `/clr` 编译，并且在该应用程序退出主函数后调用报告函数，那么报告函数调用任意的 CRT 函数，CLR将抛出异常。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_CrtSetReportHook2`|\<CRTDBG.H\>|\<errno.h\>|  
|`_CrtSetReportHookW2`|\<CRTDBG.H\>|\<errno.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## 示例  
  
```  
// crt_setreporthook2.c  
#include <windows.h>  
#include <stdio.h>  
#include <crtdbg.h>  
#include <assert.h>  
  
int __cdecl TestHook1(int nReportType, char* szMsg, int* pnRet)  
{  
   int nRet = FALSE;  
  
   printf("CRT report hook 1.\n");  
   printf("CRT report type is \"");  
   switch (nReportType)  
   {  
      case _CRT_ASSERT:  
      {  
         printf("_CRT_ASSERT");  
         // nRet = TRUE;   // Always stop for this type of report  
         break;  
      }  
  
      case _CRT_WARN:  
      {  
         printf("_CRT_WARN");  
         break;  
      }  
  
      case _CRT_ERROR:  
      {  
         printf("_CRT_ERROR");  
         break;  
      }  
  
      default:  
      {  
         printf("???Unknown???");  
         break;  
      }  
   }  
  
   printf("\".\nCRT report message is:\n\t");  
   printf(szMsg);  
  
   if   (pnRet)  
      *pnRet = 0;  
  
   return   nRet;  
}  
  
int __cdecl   TestHook2(int nReportType, char* szMsg, int* pnRet)  
{  
   int   nRet = FALSE;  
  
   printf("CRT report hook 2.\n");  
   printf("CRT report type is \"");  
   switch   (nReportType)  
   {  
      case _CRT_WARN:  
      {  
         printf("_CRT_WARN");  
         break;  
      }  
  
      case _CRT_ERROR:  
      {  
         printf("_CRT_ERROR");  
         break;  
      }  
  
      case _CRT_ASSERT:  
      {  
         printf("_CRT_ASSERT");  
         nRet = TRUE;   // Always stop for this type of report  
         break;  
      }  
  
      default:  
      {  
         printf("???Unknown???");  
         break;  
      }  
   }  
  
   printf("\".\nCRT report message is: \t");  
   printf(szMsg);  
  
   if   (pnRet)  
      *pnRet = 0;  
   // printf("CRT report code is %d.\n", *pnRet);  
   return   nRet;  
}  
  
int   main(int argc, char* argv[])  
{  
   int   nRet = 0;  
  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1)"  
          " returned %d\n", nRet);  
  
   _ASSERT(0);  
  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1)"  
          " returned %d\n", nRet);  
  
   return   nRet;  
}  
```  
  
## Output  
  
```  
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1) returned 0  
```  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)
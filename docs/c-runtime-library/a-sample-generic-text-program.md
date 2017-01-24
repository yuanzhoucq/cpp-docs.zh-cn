---
title: "简单一般文本项目 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_TCHAR 类型"
  - "映射, TCHAR.H 数据类型"
  - "一般文本示例 [CRT]"
  - "TCHAR 类型"
  - "TCHAR.H 数据类型, 映射"
ms.assetid: a03de0db-8118-4bd9-a03f-640e8dfc5ed3
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 简单一般文本项目
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 以下程序，GENTEXT.C提供的更详细的 TCHAR.H 图中定义的一般文本映射：  
  
```  
// GENTEXT.C  
// use of generic-text mappings defined in TCHAR.H  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <direct.h>  
#include <errno.h>  
#include <tchar.h>  
  
int __cdecl _tmain(int argc, _TCHAR **argv, _TCHAR **envp)  
{  
   _TCHAR buff[_MAX_PATH];  
   _TCHAR *str = _T("Astring");  
   char *amsg = "Reversed";  
   wchar_t *wmsg = L"Is";  
  
#ifdef _UNICODE  
   printf("Unicode version\n");  
#else /* _UNICODE */  
#ifdef _MBCS  
   printf("MBCS version\n");  
#else  
   printf("SBCS version\n");  
#endif  
#endif /* _UNICODE */  
  
   if (_tgetcwd(buff, _MAX_PATH) == NULL)  
       printf("Can't Get Current Directory - errno=%d\n", errno);  
   else  
       _tprintf(_T("Current Directory is '%s'\n"), buff);  
   _tprintf(_T("'%s' %hs %ls:\n"), str, amsg, wmsg);  
   _tprintf(_T("'%s'\n"), _tcsrev(_tcsdup(str)));  
   return 0;  
}  
  
```  
  
 如果已定义 `_MBCS`，GENTEXT.C 对下面程序 MBCS 的映射：  
  
```  
// crt_mbcsgtxt.c  
  
/*   
 * Use of generic-text mappings defined in TCHAR.H  
 * Generic-Text-Mapping example program  
 * MBCS version of GENTEXT.C  
 */  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <mbstring.h>  
#include <direct.h>  
  
int __cdecl main(int argc, char **argv, char **envp)  
{  
   char buff[_MAX_PATH];  
   char *str = "Astring";  
   char *amsg = "Reversed";  
   wchar_t *wmsg = L"Is";  
  
   printf("MBCS version\n");  
  
   if (_getcwd(buff, _MAX_PATH) == NULL) {  
       printf("Can't Get Current Directory - errno=%d\n", errno);  
   }  
   else {  
       printf("Current Directory is '%s'\n", buff);  
   }  
  
   printf("'%s' %hs %ls:\n", str, amsg, wmsg);  
   printf("'%s'\n", _mbsrev(_mbsdup((unsigned char*) str)));  
   return 0;  
}  
```  
  
 如果已定义 `_UNICODE`，GENTEXT.C 对程序的以下映射的 Unicode 版本。  有关使用 `wmain` 的更多信息在 Unicode 程序用作替换 `main`，请参见位于 *C 语言参考的*[使用 wmain](../c-language/using-wmain.md)。  
  
```  
// crt_unicgtxt.c  
  
/*   
 * Use of generic-text mappings defined in TCHAR.H  
 * Generic-Text-Mapping example program  
 * Unicode version of GENTEXT.C  
 */  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <direct.h>  
  
int __cdecl wmain(int argc, wchar_t **argv, wchar_t **envp)  
{  
   wchar_t buff[_MAX_PATH];  
   wchar_t *str = L"Astring";  
   char *amsg = "Reversed";  
   wchar_t *wmsg = L"Is";  
  
   printf("Unicode version\n");  
  
   if (_wgetcwd(buff, _MAX_PATH) == NULL) {  
      printf("Can't Get Current Directory - errno=%d\n", errno);  
   }  
   else {  
       wprintf(L"Current Directory is '%s'\n", buff);  
   }  
  
   wprintf(L"'%s' %hs %ls:\n", str, amsg, wmsg);  
   wprintf(L"'%s'\n", wcsrev(wcsdup(str)));  
   return 0;  
}  
```  
  
 如果 `_MBCS` 和 `_UNICODE` 未定义，ASCII 的 GENTEXT.C 映射到单字节代码，如下所示：  
  
```  
// crt_sbcsgtxt.c  
/*   
 * Use of generic-text mappings defined in TCHAR.H  
 * Generic-Text-Mapping example program  
 * Single-byte (SBCS) Ascii version of GENTEXT.C  
 */  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <direct.h>  
  
int __cdecl main(int argc, char **argv, char **envp)  
{  
   char buff[_MAX_PATH];  
   char *str = "Astring";  
   char *amsg = "Reversed";  
   wchar_t *wmsg = L"Is";  
  
   printf("SBCS version\n");  
  
   if (_getcwd(buff, _MAX_PATH) == NULL) {  
       printf("Can't Get Current Directory - errno=%d\n", errno);  
   }  
   else {  
       printf("Current Directory is '%s'\n", buff);  
   }  
  
   printf("'%s' %hs %ls:\n", str, amsg, wmsg);  
   printf("'%s'\n", strrev(strdup(str)));  
   return 0;  
}  
```  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [一般文本映射](../c-runtime-library/generic-text-mappings.md)   
 [数据类型映射](../c-runtime-library/data-type-mappings.md)   
 [常量和全局变量映射](../c-runtime-library/constant-and-global-variable-mappings.md)   
 [例程映射](../c-runtime-library/routine-mappings.md)   
 [使用一般文本映射](../c-runtime-library/using-generic-text-mappings.md)
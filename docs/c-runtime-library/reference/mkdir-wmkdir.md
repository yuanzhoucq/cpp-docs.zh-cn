---
title: "_mkdir、_wmkdir | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wmkdir"
  - "_mkdir"
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
  - "_mkdir"
  - "tmkdir"
  - "_tmkdir"
  - "wmkdir"
  - "_wmkdir"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mkdir 函数"
  - "_tmkdir 函数"
  - "_wmkdir 函数"
  - "[C++], 创建"
  - "文件夹 [C++], 创建"
  - "mkdir 函数"
  - "tmkdir 函数"
  - "wmkdir 函数"
ms.assetid: 7f22d01d-63a5-4712-a6e7-d34878b2d840
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mkdir、_wmkdir
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建一个新目录。  
  
## 语法  
  
```  
  
      int _mkdir(  
   const char *dirname   
);  
int _wmkdir(  
   const wchar_t *dirname   
);  
```  
  
#### 参数  
 `dirname`  
 新目录的路径。  
  
## 返回值  
 如果创建新目录，每个这些函数都返回值 0。  对于错误，返回函数 \- 1 并如下设置 `errno`。  
  
 `EEXIST`  
 因为 `dirname` 为现有文件名、目录名或设备名，所以目录未被创建。  
  
 `ENOENT`  
 找不到路径 。  
  
 有关这些属性和其他的更多信息返回代码示例，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_mkdir` 函数创建新目录具有指定的 *dirname。* `_mkdir` 每调用一次只能创建一个新目录，因此只有 `dirname` 的最后一个组件可以命名一个新目录。  `_mkdir` 不会转换路径分隔符。  在 Windows NT，运行时实例中反斜杠 \(\\\)、正斜杠 \(\/\/\) 都是字符串的有效路径分隔符。  
  
 `_wmkdir` 是 `_mkdir` 的宽字符版本；`_wmkdir` 的 `dirname` 参数是宽字符字符串。  `_wmkdir` 和 `_mkdir` 行为相同，否则。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tmkdir`|`_mkdir`|`_mkdir`|`_wmkdir`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_mkdir`|\<direct.h\>|  
|`_wmkdir`|\<direct.h\> or \<wchar.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_makedir.c  
  
#include <direct.h>  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   if( _mkdir( "\\testtmp" ) == 0 )  
   {  
      printf( "Directory '\\testtmp' was successfully created\n" );  
      system( "dir \\testtmp" );  
      if( _rmdir( "\\testtmp" ) == 0 )  
        printf( "Directory '\\testtmp' was successfully removed\n"  );  
      else  
         printf( "Problem removing directory '\\testtmp'\n" );  
   }  
   else  
      printf( "Problem creating directory '\\testtmp'\n" );  
}  
```  
  
## 示例输出  
  
```  
Directory '\testtmp' was successfully created  
 Volume in drive C has no label.  
 Volume Serial Number is E078-087A  
  
 Directory of C:\testtmp  
  
02/12/2002  09:56a      <DIR>          .  
02/12/2002  09:56a      <DIR>          ..  
               0 File(s)              0 bytes  
               2 Dir(s)  15,498,690,560 bytes free  
Directory '\testtmp' was successfully removed  
```  
  
## .NET Framework 等效项  
  
-   [System::IO::Directory::CreateDirectory](https://msdn.microsoft.com/en-us/library/system.io.directory.createdirectory.aspx)  
  
-   [System::IO::DirectoryInfo::CreateSubdirectory](https://msdn.microsoft.com/en-us/library/system.io.directoryinfo.createsubdirectory.aspx)  
  
## 请参阅  
 [目录控制](../../c-runtime-library/directory-control.md)   
 [\_chdir、\_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [\_rmdir、\_wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)
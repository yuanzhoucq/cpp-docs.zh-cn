---
title: "rename、_wrename | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "rename"
  - "_wrename"
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
  - "_wrename"
  - "_trename"
  - "Rename"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_trename 函数"
  - "_wrename 函数"
  - "[C++], 重命名"
  - "文件 [C++], 重命名"
  - "名称 [C++], 更改目录"
  - "名称 [C++], 更改文件"
  - "rename 函数"
  - "重命名目录"
  - "重命名文件"
  - "trename 函数"
  - "wrename 函数"
ms.assetid: 9f0a6103-26a2-4dda-b14b-79a48946266a
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# rename、_wrename
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重命名或移动目录。  
  
## 语法  
  
```  
  
      int rename(  
   const char *oldname,  
   const char *newname   
);  
int _wrename(  
   const wchar_t *oldname,  
   const wchar_t *newname   
);  
```  
  
#### 参数  
 *oldname*  
 对旧名称上。  
  
 *newname*  
 为新的名称上。  
  
## 返回值  
 如果成功，这些函数中的每个表达式都返回 0。  在错误，则函数将返回非零值并将 `errno` 设置为以下值之一：  
  
 `EACCES`  
 *newname* 指定的文件或目录已存在或无法创建 \(无效的路径\);或者 *oldname* 是目录，并 *newname* 指定一个路径。  
  
 `ENOENT`  
 *oldname* 或路径指定的文件未找到。  
  
 `EINVAL`  
 包含无效字符。  
  
 有关其他可能返回值的，请参见 [\_doserrno、\_errno、syserrlist 和\_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 **重命名** 函数使 *oldname* 或目录。名称指定的文件添加到 *newname*给定的名称。  旧名称必须是现有文件或目录的路径。  新名称不能与现有文件或目录的名称。  可以使用 **重命名** 将文件从一个目录或设备到另一个 *newname* 通过指定参数的其他路径。  但是，不能使用 **重命名** 移动目录。  可以重命名目录，但不会移动。  
  
 `_wrename` 是 `的宽字符版本；_wrename` 的指针参数是宽字符串。  除此以外，`_wrename` 和  的行为完全相同。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE& 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_trename`|**重命名**|**重命名**|`_wrename`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|**重命名**|\<io.h\> or \<stdio.h\>|  
|`_wrename`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_renamer.c  
/* This program attempts to rename a file named  
 * CRT_RENAMER.OBJ to CRT_RENAMER.JBO. For this operation  
 * to succeed, a file named CRT_RENAMER.OBJ must exist and  
 * a file named CRT_RENAMER.JBO must not exist.  
 */  
  
#include <stdio.h>  
  
int main( void )  
{  
   int  result;  
   char old[] = "CRT_RENAMER.OBJ", new[] = "CRT_RENAMER.JBO";  
  
   /* Attempt to rename file: */  
   result = rename( old, new );  
   if( result != 0 )  
      printf( "Could not rename '%s'\n", old );  
   else  
      printf( "File '%s' renamed to '%s'\n", old, new );  
}  
```  
  
## Output  
  
```  
File 'CRT_RENAMER.OBJ' renamed to 'CRT_RENAMER.JBO'  
```  
  
## .NET Framework 等效项  
 [System.IO.File::Exists](https://msdn.microsoft.com/en-us/library/system.io.file.move.aspx)  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)
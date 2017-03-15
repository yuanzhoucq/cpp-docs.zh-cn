---
title: "_rmdir、_wrmdir | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wrmdir"
  - "_rmdir"
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
  - "trmdir"
  - "_trmdir"
  - "wrmdir"
  - "_rmdir"
  - "_wrmdir"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_rmdir 函数"
  - "_trmdir 函数"
  - "_wrmdir 函数"
  - "[C++], 删除"
  - "[C++], 移除"
  - "rmdir 函数"
  - "trmdir 函数"
  - "wrmdir 函数"
ms.assetid: 652c2a5a-b0ac-4493-864e-1edf484333c5
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _rmdir、_wrmdir
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

删除目录。  
  
## 语法  
  
```  
  
      int _rmdir(  
   const char *dirname   
);  
int _wrmdir(  
   const wchar_t *dirname   
);  
```  
  
#### 参数  
 `dirname`  
 删除目录路径。  
  
## 返回值  
 如果目录成功被删除，则这些函数返回0。  返回值 \- 1 表示一个错误并将 `errno` 设置为以下值之一：  
  
 **ENOTEMPTY**  
 特定路径并非目录，目录不为空，或者目录是当前工作目录或根目录。  
  
 `ENOENT`  
 路径无效。  
  
 **EACCES**  
 程序有一个打开处理程序到目录中。  
  
 有关这些属性和其他的更多信息返回代码示例，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_rmdir` 函数删除通过`dirname` 指定的目录。  目录必须为空，并且不能为当前工作目录或根目录。  
  
 `_wrmdir` 是 `_rmdir` 的宽字符版本；`_wrmdir` 的 `dirname` 参数是宽字符字符串。  `_wrmdir` 和 `_rmdir` 行为相同，否则。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_trmdir`|`_rmdir`|`_rmdir`|`_wrmdir`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_rmdir`|\<direct.h\>|  
|`_wrmdir`|\<direct.h\> or \<wchar.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
 请参阅 [\_mkdir](../../c-runtime-library/reference/mkdir-wmkdir.md) 示例。  
  
## .NET Framework 等效项  
 [System::IO::Directory::Delete](https://msdn.microsoft.com/en-us/library/system.io.directory.delete.aspx)  
  
## 请参阅  
 [目录控制](../../c-runtime-library/directory-control.md)   
 [\_chdir、\_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [\_mkdir、\_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)
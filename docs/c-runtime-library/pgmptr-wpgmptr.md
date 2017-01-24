---
title: "_pgmptr、_wpgmptr | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pgmptr"
  - "_pgmptr"
  - "wpgmptr"
  - "_wpgmptr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_pgmptr 函数"
  - "_wpgmptr 函数"
  - "pgmptr 函数"
  - "wpgmptr 函数"
ms.assetid: 4d44b515-0eff-4136-8bc4-684195f218f5
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _pgmptr、_wpgmptr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可执行文件的路径。  弃用；使用 [\_get\_pgmptr](../c-runtime-library/reference/get-pgmptr.md) 和 [\_get\_wpgmptr](../c-runtime-library/reference/get-wpgmptr.md)。  
  
## 语法  
  
```  
extern char *_pgmptr;  
extern wchar_t *_wpgmptr;  
```  
  
## 备注  
 当程序解释器从命令行\(Cmd.exe \) 运行时，`_pgmptr` 会自动初始化为可执行文件的完整路径。  例如，如果Hello.exe在C:\\BIN中，C:\\BIN 在路径中，要执行时，将`_pgmptr` 设置为 C:\\BIN\\Hello.exe：  
  
```  
C> hello   
```  
  
 当程序时不是从命令行运行，`_pgmptr` 可能被初始化为程序名称 \(不带文件扩展名的文件的基本名称\) 或文件名、相对路径或完整路径。  
  
 `_wpgmptr`是`_pgmptr` 的宽字符副本，用于使用 `wmain`的程序。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|  
  
## 要求  
  
|变量|必需的标头|  
|--------|-----------|  
|`_pgmptr`, `_wpgmptr`|\<stdlib.h\>|  
  
## 示例  
 下面的程序说明 `_pgmptr` 的用法。  
  
```  
// crt_pgmptr.c  
// compile with: /W3  
// The following program demonstrates the use of _pgmptr.  
//  
#include <stdio.h>  
#include <stdlib.h>  
int main( void )  
{  
   printf("The full path of the executing program is : %Fs\n",   
     _pgmptr); // C4996  
   // Note: _pgmptr is deprecated; use _get_pgmptr instead  
}  
```  
  
 可以通过更改 `%Fs`为`%S` ，更改`main`为 `wmain`，使用`_wpgmptr`。  
  
## 请参阅  
 [全局变量](../c-runtime-library/global-variables.md)
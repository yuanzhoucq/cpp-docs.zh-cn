---
title: "__getmainargs、__wgetmainargs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__wgetmainargs"
  - "__getmainargs"
apilocation: 
  - "msvcr100.dll"
  - "msvcrt.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__wgetmainargs"
  - "__getmainargs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__wgetmainargs"
  - "__getmainargs"
ms.assetid: f72f54eb-9509-4bdf-8752-40fc49055439
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# __getmainargs、__wgetmainargs
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过传入的指针，调用命令行解析和拷贝参数到`main()`。  
  
## 语法  
  
```cpp  
int __getmainargs(  
    int * _Argc,   
   char *** _Argv,   
   char *** _Env,   
   int _DoWildCard,  
_startupinfo * _StartInfo);  
  
 int __wgetmainargs (  
   int *_Argc,  
   wchar_t ***_Argv,  
   wchar_t ***_Env,  
   int _DoWildCard,  
   _startupinfo * _StartInfo)  
  
```  
  
#### 参数  
 `_Argc`  
 包含 `argv` 后面的参数计数的整数。  `argc` 参数始终大于或等于 1。  
  
 `_Argv`  
 表示由杂注用户输入的命令行参数的以 null 结尾的字符串的数组。  按照约定，`argv[0]`是用于调用程序的命令， argv\[1\] 是第一个命令行参数，依此类推，直到argv\[argc\]，它始终为 NULL。  第一个命令行参数始终是  `argv[1]`，且最后一个命令行参数是 `argv[argc – 1]`。  
  
 `_Env`  
 表示用户环境中的变量集的字符串的数组。  该数组由 NULL 项终止。  
  
 `_DoWildCard`  
 如果整数，设置为 1。扩展命令行参数的通配符，或者，如果设置要么为 0 不执行。  
  
 `_StartInfo`  
 将传递给CRT DLL的任何其他信息。。  
  
## 返回值  
 如果成功，则为0 ；如果不成功，则负值。  
  
## 备注  
 在非宽字符平台上使用`__getmainargs`，宽字符\(Unicode\)平台上使用`__wgetmainargs`  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|\_\_getmainargs|internal.h|  
|\_\_wgetmainargs|internal.h|
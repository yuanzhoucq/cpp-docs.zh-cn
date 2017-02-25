---
title: "_inp、_inpw、_inpd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_inp"
  - "_inpw"
  - "_inpd"
apilocation: 
  - "msvcrt.dll"
  - "msvcr120.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "inpd"
  - "_inp"
  - "_inpw"
  - "_inpd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_inp 函数"
  - "_inpd 函数"
  - "_inpw 函数"
  - "I/O [CRT], 端口"
  - "inp 函数"
  - "inpd 函数"
  - "inpw 函数"
  - "端口, I/O 例程"
ms.assetid: 5d9c2e38-fc85-4294-86d5-7282cc02d1b3
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _inp、_inpw、_inpd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从某个端口输入一个字节 \(`_inp`\)、一个字 \(`_inpw`\) 或一个双字 \(`_inpd`\)。  
  
> [!IMPORTANT]
>  这些函数已过时。 从 Visual Studio 2015 开始，CRT 中不再提供这些函数。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[不支持 \/ZW 的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
int _inp(   
   unsigned short port   
);  
unsigned short _inpw(   
   unsigned short port   
);  
unsigned long _inpd(   
   unsigned short port   
);  
```  
  
#### 参数  
 `port`  
 I\/O 端口号。  
  
## 返回值  
 这些函数返回从 `port` 中读取的字节、字或双字。 无错误返回。  
  
## 备注  
 `_inp`、`_inpw` 和 `_inpd` 函数分别从指定的输入端口读取一个字节、一个字和一个双字。 输入值可以是 0 – 65,535 范围内的任何无符号短整数。  
  
 由于这些函数直接从 I\/O 端口读取内容，因此它们可能无法在 Windows NT、Windows 2000、Windows XP 和 Windows Server 2003 的用户代码中使用。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_inp`|\<conio.h\>|  
|`_inpw`|\<conio.h\>|  
|`_inpd`|\<conio.h\>|  
  
 有关更多兼容性信息，请参阅[兼容性](../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [控制台和端口 I\/O](../c-runtime-library/console-and-port-i-o.md)   
 [\_outp、\_outpw、\_outpd](../c-runtime-library/outp-outpw-outpd.md)
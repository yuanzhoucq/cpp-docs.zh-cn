---
title: "fwide | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fwide"
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
  - "fwide"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fwide 函数"
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# fwide
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

尚未实现。  
  
## 语法  
  
```  
int fwide(  
   FILE *stream,  
   int mode;  
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE` 结构的指针（忽略）。  
  
 `mode`  
 流的新宽度：宽字符的正，负用于字节，零不更改退出。（忽略此值。）  
  
## 返回值  
 此当前函数返回 `mode`。  
  
## 备注  
 此函数的当前版本不符合标准。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`fwide`|\<wchar.h\>|  
  
 有关更多信息，请参见[Compatibility](../../c-runtime-library/compatibility.md)。
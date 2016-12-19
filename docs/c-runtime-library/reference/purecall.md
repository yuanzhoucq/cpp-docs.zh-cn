---
title: "_purecall | Microsoft Docs"
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
  - "_purecall"
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
  - "purecall"
  - "_purecall"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_purecall 函数"
  - "purecall 函数"
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _purecall
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

默认纯虚函数调用错误处理程序中。 编译器将生成代码以调用此函数，当调用纯虚成员函数。  
  
## 语法  
  
```  
extern "C" int __cdecl _purecall();  
```  
  
## 备注  
 `_purecall` 函数是 Microsoft Visual c \+ \+ 编译器的 Microsoft 专用实现详细信息。 此函数不是为了您的代码直接调用，并且还没有公共标题声明。 因为它是一个公共导出的 C 运行库，它是此处介绍。  
  
 对一个纯虚函数的调用是一个错误，因为它不具有实现。 编译器生成的代码来调用 `_purecall` 错误处理程序函数调用纯虚函数时。 默认情况下， `_purecall` 终止程序。 之前终止， `_purecall` 函数将调用 `_purecall_handler` 如果已设置了一个进程正常工作。 您可以安装纯虚函数调用，以将其进行调试或报告的数据捕获您自己错误处理程序函数。 若要使用您自己的错误处理程序，创建一个具有函数 `_purecall_handler` 签名，然后使用 [\_set\_purecall\_handler](../../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md) 以使其当前处理程序。  
  
## 要求  
 `_purecall` 函数没有标头声明。`_purecall_handler` \< Stdlib.h \> 中定义 typedef。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [\_get\_purecall\_handler \_set\_purecall\_handler](../../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)
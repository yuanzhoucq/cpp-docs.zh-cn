---
title: "__p__commode | Microsoft Docs"
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
  - "__p__commode"
apilocation: 
  - "msvcr110.dll"
  - "msvcrt.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__p__commode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__p__commode"
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
caps.latest.revision: 2
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __p__commode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指向`_commode` 全局变量，它为文件 I\/O 操作指定默认 *文件提交模式*。  
  
## 语法  
  
```cpp  
int * __p__commode(  
   );  
```  
  
## 返回值  
 指向 `_commode` 全局变量的指针。  
  
## 备注  
 `__p__commode` 函数仅供内部使用，用户代码不应调用它。  
  
 关键数据时写入磁盘时，指定文件提交模式。  有关详细信息，请参阅[fflush](../c-runtime-library/reference/fflush.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|\_\_p\_\_commode|internal.h|
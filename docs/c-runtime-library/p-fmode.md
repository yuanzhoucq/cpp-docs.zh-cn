---
title: "__p__fmode | Microsoft Docs"
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
  - "__p__fmode"
apilocation: 
  - "msvcr80.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcrt.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__p__fmode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__p__fmode"
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __p__fmode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指向`_fmode` 全局变量的指针，它为文件 I\/O 操作指定默认 *文件提交模式*。  
  
## 语法  
  
```cpp  
int* __p__fmode(  
   );  
```  
  
## 返回值  
 指向 `_fmode` 全局变量的指针。  
  
## 备注  
 `__p__fmode` 函数仅供内部使用，用户代码不应调用它。  
  
 特定模式的文件。[\_open](../c-runtime-library/reference/open-wopen.md) [\_pipe](../c-runtime-library/reference/pipe.md) 和 I\/O 操作指定 `binary` 或 `text` 转换。  有关详细信息，请参阅[\_fmode](../c-runtime-library/fmode.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|\_\_p\_\_fmode|stdlib.h|
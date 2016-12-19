---
title: "towctrans | Microsoft Docs"
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
  - "towctrans"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "towctrans"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "towctrans 函数"
ms.assetid: 1ed1e70d-7b31-490f-a7d9-42564b5924ca
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# towctrans
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

转换字符。  
  
## 语法  
  
```  
wint_t towctrans(  
   wint_t c,  
   wctrans_t category   
);  
```  
  
#### 参数  
 `c`  
 要转换的字符。  
  
 `category`  
 包含 [wctrans](../../c-runtime-library/reference/wctrans.md)返回值的标识符。  
  
## 返回值  
 `towctrans` 后面的 `c`字符，`category`使用的转换规则。  
  
## 备注  
 绑定由对 [wctrans](../../c-runtime-library/reference/wctrans.md)的早期的成功调用 `category` 的返回值。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`towctrans`|\<wctype.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 使用 `towctrans`的示例参见 `wctrans`。  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)
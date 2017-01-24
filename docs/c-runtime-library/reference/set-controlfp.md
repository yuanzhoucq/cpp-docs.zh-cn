---
title: "_set_controlfp | Microsoft Docs"
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
  - "_set_controlfp"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "set_controlfp"
  - "_set_controlfp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_controlfp 函数"
  - "浮点函数, 设置控制字"
  - "set_controlfp 函数"
ms.assetid: e0689d50-f68a-4028-a9c1-fb23eedee4ad
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_controlfp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置浮点控制字。  
  
## 语法  
  
```  
void __cdecl _set_controlfp(  
    unsigned int newControl,  
    unsigned int mask  
);  
```  
  
#### 参数  
 `newControl`  
 新的控制字位值。  
  
 `mask`  
 设置新的控制字位的掩码。  
  
## 返回值  
 无。  
  
## 备注  
 `_set_controlfp` 与 `_control87`相似，但是，它只设置浮点控制字为 `newControl`。  按位值指示浮点控制态。  浮点控制允许程序状态更改精度、舍入和 INFINITY 模式在浮点数学包。  还可以使用 `_set_controlfp` 掩码或非掩码浮点异常。  有关详细信息，请参阅[\_control87、\_controlfp、\_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)。  
  
 当使用 [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md) 或 `/clr:pure` 编译时，这些函数被丢弃，因为公共语言运行时 \(CLR\) 仅支持默认值浮点精度。  
  
## 要求  
  
|例程|必需的标头|兼容性|  
|--------|-----------|---------|  
|`_set_controlfp`|\<float.h\>|仅限 x86 处理器|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [\_clear87、\_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [\_status87, \_statusfp, \_statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)
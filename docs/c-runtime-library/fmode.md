---
title: "_fmode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "fmode"
  - "_fmode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "文件翻译 [C++], 默认模式"
  - "fmode 函数"
  - "_fmode 函数"
ms.assetid: ac6df9eb-e5cc-4c54-aff3-373c21983118
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# _fmode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`_fmode` 变量设置文本文件的默认模式或二进制转换。  此全局变量因有更安全函数版本 [\_set\_fmode](../c-runtime-library/reference/set-fmode.md)[\_get\_fmode](../c-runtime-library/reference/get-fmode.md) 而被废弃，这被使用来替代全局变量。  按如下方式在 Stdlib.h 声明。  
  
## 语法  
  
```  
extern int _fmode;  
```  
  
## 备注  
 `_fmode` 的默认设置是文本方式转换的 `_O_TEXT` 。  `_O_BINARY` 模式是二进制的设置。  
  
 可以通过三种方式更改 `_fmode` 的值：  
  
-   与 Binmode.obj 的链接。  这会更改初始 `_fmode` 设置为 `_O_BINARY`，则所有文件，除 `stdin`以二进制模式中打开 `stdout`和 `stderr`。  
  
-   分别调用 `_get_fmode` 或 `_set_fmode` 获取或设置 `_fmode` 全局变量。  
  
-   直接在程序中更改它的 `_fmode` 值。  
  
## 请参阅  
 [全局变量](../c-runtime-library/global-variables.md)   
 [\_get\_fmode](../c-runtime-library/reference/get-fmode.md)   
 [\_set\_fmode](../c-runtime-library/reference/set-fmode.md)
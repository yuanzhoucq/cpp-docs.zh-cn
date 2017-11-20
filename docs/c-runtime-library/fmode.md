---
title: "_fmode |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- fmode
- _fmode
dev_langs: C++
helpviewer_keywords:
- file translation [C++], default mode
- fmode function
- _fmode function
ms.assetid: ac6df9eb-e5cc-4c54-aff3-373c21983118
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9007cceacb150b13796e395799f2037704976802
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="fmode"></a>_fmode
`_fmode` 变量为文本或二进制转换设置默认文件转换模式。 此全局变量已被弃用，因为出现了更安全的函数版本 [_get_fmode](../c-runtime-library/reference/get-fmode.md) 和 [_set_fmode](../c-runtime-library/reference/set-fmode.md)，应使用这两个版本来替换此全局变量。 在 Stdlib.h 中按如下方式进行声明。  
  
## <a name="syntax"></a>语法  
  
```  
extern int _fmode;  
```  
  
## <a name="remarks"></a>备注  
 `_fmode` 的默认设置是适用于文本模式转换的 `_O_TEXT`。 `_O_BINARY` 是适用于二进制模式的设置。  
  
 可以按以下三种方式更改 `_fmode` 的值：  
  
-   与 Binmode.obj 链接。这会将 `_fmode` 的初始设置更改为 `_O_BINARY`，从而导致除 `stdin`、`stdout`，和 `stderr` 以外的所有文件在二进制模式下打开。  
  
-   调用 `_get_fmode` 或 `_set_fmode` 以分别获取或设置 `_fmode` 全局变量。  
  
-   通过在程序中设置来直接更改 `_fmode` 的值。  
  
## <a name="see-also"></a>另请参阅  
 [全局变量](../c-runtime-library/global-variables.md)   
 [_get_fmode](../c-runtime-library/reference/get-fmode.md)   
 [_set_fmode](../c-runtime-library/reference/set-fmode.md)
---
title: "文件位置错误 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ebbb6ab903db73fce84059af567dd5e80dfb3afb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="file-position-errors"></a>文件位置错误
**ANSI 4.9.9.1, 4.9.9.4** 失败时，`fgetpos` 或 `ftell` 函数设置的宏 `errno` 的值  
  
 当 `fgetpos` 或 `ftell` 失败时，`errno` 将设置为清单常量 `EINVAL`（如果位置无效）或 EBADF（如果文件数量错误）。 常量是在 ERRNO.H 中定义的。  
  
## <a name="see-also"></a>另请参阅  
 [库函数](../c-language/library-functions.md)
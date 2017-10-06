---
title: "文件位置错误 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: f81176b3b92b7ab92954947bb98e3bd14b93a290
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="file-position-errors"></a>文件位置错误
**ANSI 4.9.9.1, 4.9.9.4** 失败时，`fgetpos` 或 `ftell` 函数设置的宏 `errno` 的值  
  
 当 `fgetpos` 或 `ftell` 失败时，`errno` 将设置为清单常量 `EINVAL`（如果位置无效）或 EBADF（如果文件数量错误）。 常量是在 ERRNO.H 中定义的。  
  
## <a name="see-also"></a>另请参阅  
 [库函数](../c-language/library-functions.md)

---
title: "转换模式常量 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _O_BINARY
- _O_TEXT
- _O_RAW
dev_langs: C++
helpviewer_keywords:
- O_BINARY constant
- O_TEXT constant
- O_RAW constant
- _O_TEXT constant
- _O_RAW constant
- translation constants
- _O_BINARY constant
- translation, constants
- translation, modes
- translation modes (file I/O)
ms.assetid: a5993bf4-7e7a-47f9-83c3-e46332b85579
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8f5224064158dcbcb277524af21a0059a324fbc5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="translation-mode-constants"></a>翻译模式常量
## <a name="syntax"></a>语法  
  
```  
  
#include <fcntl.h>  
  
```  
  
## <a name="remarks"></a>备注  
 `_O_BINARY` 和 `_O_TEXT` 清单常数将决定文件（`_open` 和 `_sopen`）的转换模式或流 (`_setmode`) 的转换模式。  
  
 允许的值包括：  
  
 `_O_TEXT`  
 在文本（已转换）模式下打开文件。 输入时回车-换行符 (CR-LF) 组合将转换为单个换行符 (LF)。 输出时换行符将转换为 CR-LF 组合。 CTRL+Z 也将在输入时解释为文件尾字符。 在打开以进行读取或读取/写入的文件中，`fopen` 将检查文件末尾的 Ctrl+Z 并在可能的情况下将其移除。 这样做是因为，使用 `fseek` 和 `ftell` 函数在以 Ctrl+Z 结尾的文件中移动时，可能导致 `fseek` 在文件末尾附近错误操作。  
  
 `_O_BINARY`  
 在二进制（未转换）模式下打开文件。 禁止上述的转换。  
  
 `_O_RAW`  
 与 `_O_BINARY` 相同。 支持 C 2.0 兼容性。  
  
 有关详细信息，请参阅[文本和二进制模式文件 I/O](../c-runtime-library/text-and-binary-mode-file-i-o.md) 和[文件转换](../c-runtime-library/file-translation-constants.md)。  
  
## <a name="see-also"></a>另请参阅  
 [_open、_wopen](../c-runtime-library/reference/open-wopen.md)   
 [_pipe](../c-runtime-library/reference/pipe.md)   
 [_sopen、_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [_setmode](../c-runtime-library/reference/setmode.md)   
 [全局常量](../c-runtime-library/global-constants.md)
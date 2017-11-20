---
title: "对预处理器的指令 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 39f1e29a2bc8b72d5b2467c248a4d12b63baa26b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="directives-to-the-preprocessor"></a>对预处理器的指令
“指令”指示 C 预处理器在编译之前先对程序的文本执行特定操作。 《预处理器参考》中完整描述了[预处理器指令](../preprocessor/preprocessor-directives.md)。 本示例使用预处理器指令 `#define`：  
  
```  
#define MAX 100  
```  
  
 该语句告知编译器在编译前将 `MAX` 的每个匹配项替换为 `100`。 C 编译器预处理器指令为：  
  
|#define|#endif|#ifdef|#line|  
|--------------|-------------|-------------|------------|  
|`#elif`|`#error`|#ifndef|**#pragma**|  
|`#else`|`#if`|`#include`|`#undef`|  
  
## <a name="see-also"></a>另请参阅  
 [源文件和源程序](../c-language/source-files-and-source-programs.md)
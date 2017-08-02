---
title: "对预处理器的指令 | Microsoft Docs"
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
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: e5d4790cccc280a6a2d23a66c6959fd07bdefa9b
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

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

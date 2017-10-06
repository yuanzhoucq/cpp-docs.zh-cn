---
title: "字符序列 | Microsoft Docs"
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
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 67ddf6a6712e0c98ea7b7866b3267d56308a5b5c
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="character-sequences"></a>字符序列
**ANSI 3.8.2** 源文件字符序列的映射  
  
 预处理器语句使用的字符集和源文件语句相同，只不过转义序列不受支持。  
  
 因此，若要指定包含文件的路径，请仅使用一个反斜杠：  
  
```  
#include "path1\path2\myfile"  
```  
  
 在源代码中，需要两个反斜杠：  
  
```  
fil = fopen( "path1\\path2\\myfile", "rt" );  
```  
  
## <a name="see-also"></a>另请参阅  
 [预处理指令](../c-language/preprocessing-directives.md)

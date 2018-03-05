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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 09134a17ad8711169a3afc30490c188af47a3f42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>请参阅  
 [预处理指令](../c-language/preprocessing-directives.md)
---
title: "生成文件中的特殊字符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6c574040d6004516682379a5e64b87c1b92388ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="special-characters-in-a-makefile"></a>生成文件中的特殊字符
若要使用 NMAKE 特殊字符作为原义字符，请在它前面添脱字号 (^)。 NMAKE 将忽略位于其他字符之前的插入符号。 特殊字符包括：  
  
 `:  ;  #  (  )  $  ^  \  {  }  !  @  —`  
  
 带引号的字符串中的脱字号 (^) 被视为文本的插入符号字符。 在行尾的脱字号插入文本换行字符在字符串或宏中。  
  
 在宏的位置，反斜杠 (\\) 后接换行符字符替换为空格。  
  
 在命令中，百分号 （%） 是一个文件说明符。 若要表示 %按原义命令中的，指定代替一条双百分号 （%）。 在其他情况下，NMAKE 单个 %按原义解释，但它始终将双精度值 %%作为单个 %。 因此，来表示文本 %%，指定任一三个百分比符号，%%%，或四个百分比符号 %%%。  
  
 若要使用美元符号 （$） 用作原义字符命令中，指定两个美元符号 （$$）。 此方法还可在其他情况下其中 ^ $ 工作原理。  
  
## <a name="see-also"></a>请参阅  
 [生成文件的内容](../build/contents-of-a-makefile.md)
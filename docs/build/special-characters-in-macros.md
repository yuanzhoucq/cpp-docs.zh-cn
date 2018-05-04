---
title: 在宏中的特殊字符 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c271d2f39a4d81776c06a107616170192e82d40d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="special-characters-in-macros"></a>宏内的特殊字符
数字符号 （#） 后的定义来指定注释。 若要在宏中指定文本的数字符号，请使用脱字号 (^)，如在 ^ #。  
  
 美元符号 （$） 指定宏调用。 若要指定字符 $，使用 $$。  
  
 若要扩展到新行的定义，以结束行反斜杠 (\\)。 宏调用时，反斜杠和换行符字符替换为空格。 若要指定在行末尾文本反斜杠，在它前面加脱字号 (^)，或在其后加一个注释说明符 （#）。  
  
 若要指定文本换行字符，以结束行的脱字号 (^)，如：  
  
```  
CMDS = cls^  
dir  
```  
  
## <a name="see-also"></a>请参阅  
 [定义 NMAKE 宏](../build/defining-an-nmake-macro.md)
---
title: "在宏中的特殊字符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4d954abc593fcba3887da4f7ee4bd5ce1e443e18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
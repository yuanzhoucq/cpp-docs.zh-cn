---
title: "编译器警告 （等级 1） C4274 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4274
dev_langs:
- C++
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4519258a10937ad96528f34484a44d398a0cd0ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4274"></a>编译器警告 （等级 1） C4274
\#ident 忽略;请参阅文档 #pragma 注释 （exestr，'string'）  
  
 `#ident`指令，将用户指定的字符串插入的对象或可执行文件中，已弃用。 因此，编译器将忽略指令。  
  
> [!CAUTION]
>  警告 C4274 建议您使用[#pragma 注释 （exestr，'string'）](../../preprocessor/comment-c-cpp.md)指令。 但是，这一建议已弃用，并且将编译器的未来版本中对其进行修改。 如果你使用`#pragma`指令，链接器工具 (LINK.exe) 将忽略注释记录生成的指令并发出警告[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)。 而不是`#ident`指令，我们建议在你的应用程序中使用文件版本资源字符串。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   删除`#ident "`*字符串*`"`指令。  
  
## <a name="see-also"></a>请参阅  
 [注释 （C/c + +）](../../preprocessor/comment-c-cpp.md)   
 [链接器工具警告 LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)   
 [使用资源文件](../../windows/working-with-resource-files.md)
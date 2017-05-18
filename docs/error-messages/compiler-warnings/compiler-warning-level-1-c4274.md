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
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: fbba1e6dde180e77afe7ed8960849ee8cc0fd108
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4274"></a>编译器警告 （等级 1） C4274
\#ident 忽略;请参阅文档 #pragma 注释 （exestr，'string'）  
  
 `#ident`指令，插入一个用户指定的字符串对象或可执行文件，不推荐使用。 因此，编译器将忽略该指令。  
  
> [!CAUTION]
>  警告 C4274 建议您在使用[#pragma 注释 （exestr，'string'）](../../preprocessor/comment-c-cpp.md)指令。 但是，这一建议已弃用，并且程序进行修改，则编译器的未来版本中。 如果您使用`#pragma`指令时，链接器工具 (LINK.exe) 将忽略注释记录生成的指令并发出警告[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)。 而不是`#ident`指令时，我们建议在您的应用程序中使用的文件版本资源字符串。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   删除`#ident "`*字符串*`"`指令。  
  
## <a name="see-also"></a>另请参阅  
 [注释 （C/c + +）](../../preprocessor/comment-c-cpp.md)   
 [链接器工具警告 LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)   
 [使用资源文件](../../windows/working-with-resource-files.md)

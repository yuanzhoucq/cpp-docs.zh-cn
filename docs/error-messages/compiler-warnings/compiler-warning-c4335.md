---
title: "编译器警告 C4335 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4335
dev_langs:
- C++
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
caps.latest.revision: 12
author: corob-msft
ms.author: corob
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: dc8436664038d3f53f3a01d5006c41c3d0e4c8f0
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="compiler-warning-c4335"></a>编译器警告 C4335
检测到 Mac 文件格式: 请将源文件转换为 DOS 格式或 UNIX 格式  
  
 源文件的第一行的行终止字符是 Macintosh 样式 ('\r') 而不是 UNIX (\n) 或 DOS (\r\n)。  
  
 作为错误发出始终发出此警告。  请参阅[警告](../../preprocessor/warning.md)杂注有关如何禁用此警告信息。  此外，发出此警告仅一次每编译单位。 因此，如果有多个`#include`在 Macintosh 格式中指定文件的指令，C4335 将才会发出一次。  
  
 Macintosh 格式生成文件的一种方法是使用**高级保存选项**(上**文件**菜单) 在 Visual Studio 中。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4335。  
  
```  
// C4335 expected  
#include "c4335.h"   // assume both include files are in Macintosh format  
#include "c4335_2.h"  
```

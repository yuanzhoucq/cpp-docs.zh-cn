---
title: "编译器警告 C4335 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4335
dev_langs: C++
helpviewer_keywords: C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ea0a981c00a1941c3004ac820edbcbbbf0776c4c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-c4335"></a>编译器警告 C4335
检测到的 Mac 文件格式： 请将源文件转换为 DOS 或 UNIX 格式  
  
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
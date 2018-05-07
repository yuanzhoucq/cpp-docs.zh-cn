---
title: NMAKE 错误 U1033 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1033
dev_langs:
- C++
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1d39d4c35ec66d405d51d601b7c5d2b2ab37b02
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1033"></a>NMAKE 错误 U1033
语法错误: 'string' 意外  
  
 字符串不是生成文件的有效语法的一部分。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  如果结束设置的命令的尖括号 (**<<**) 为内联文件不在行开头，将出现以下错误：  
  
    ```  
    syntax error : 'EOF' unexpected  
    ```  
  
2.  如果宏定义中生成文件中包含的等号 (**=**) 没有前面名，或者如果正在定义的名称就是扩展到 nothing 的宏，将出现以下错误：  
  
    ```  
    syntax error : '=' unexpected  
    ```  
  
3.  如果分号 (**;**) 工具中的注释行中。INI 不是行的开头，将出现以下错误：  
  
    ```  
    syntax error : ';' unexpected  
    ```  
  
4.  如果将生成文件已格式化的字处理器，会出现下列错误：  
  
    ```  
    syntax error : ':' unexpected  
    ```
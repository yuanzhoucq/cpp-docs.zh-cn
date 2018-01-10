---
title: "NMAKE 错误 U1033 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1033
dev_langs: C++
helpviewer_keywords: U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 94f2626e1ce318d83d306595e386f880c62dec3e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
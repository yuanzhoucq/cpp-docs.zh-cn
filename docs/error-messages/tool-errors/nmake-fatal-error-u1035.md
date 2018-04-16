---
title: "NMAKE 错误 U1035 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U1035
dev_langs:
- C++
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0d7730f882b40c24822cb4b8e2c6a12147cacf2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1035"></a>NMAKE 错误 U1035
语法错误： 预期 ':' 或 '=' 分隔符  
  
 任一冒号 (**:**) 或等号 (**=**) 应。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  冒号没有按照目标。  
  
2.  冒号和没有空格 （例如 a:） 的后面单字母目标。 NMAKE 解释它为驱动器规范。  
  
3.  冒号没有按照推理规则。  
  
4.  宏定义不后跟一个等号。  
  
5.  字符跟在一个反斜杠 (**\\**) 用于将命令继续到一个新行。  
  
6.  一个字符串出现，没有按照任何 NMAKE 语法规则。  
  
7.  生成文件格式化的字处理器。
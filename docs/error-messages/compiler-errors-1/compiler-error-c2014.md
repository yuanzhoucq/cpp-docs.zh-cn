---
title: "编译器错误 C2014 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2014
dev_langs: C++
helpviewer_keywords: C2014
ms.assetid: 231d8e9c-48c0-4027-99a3-245d186275ec
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b5f718aee1cb7ede548719a8275ea6788b70d1c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2014"></a>编译器错误 C2014
预处理器命令必须作为第一个非空白空间启动  
  
 `#`的预处理器指令的登录必须是不是空白的行的第一个字符。  
  
 下面的示例生成 C2014:  
  
```  
// C2014.cpp  
int k; #include <stdio.h>   // C2014  
```  
  
 可能的解决方法：  
  
```  
// C2014b.cpp  
// compile with: /c  
int k;   
#include <stdio.h>  
```
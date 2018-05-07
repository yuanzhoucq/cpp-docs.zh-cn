---
title: 资源编译器错误 RC2001 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2001
dev_langs:
- C++
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ef1fd5d29fc5784ee418a8456cacec37e943b73
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-error-rc2001"></a>资源编译器错误 RC2001
常量中有换行符  
  
 字符串常量在第二个行继续没有反斜杠 (**\\**) 或关闭并打开两个双引号 (**"**)。  
  
 若要中断位于源文件中的两个行的字符串常量，执行以下操作：  
  
-   结束以行继续符，反斜杠的第一行。  
  
-   关闭与双引号匹配的第一行中的字符串，并使用另一个引号打开下一步的行中的字符串。  
  
 不满足需求，若要结束用 \n，字符串常量中嵌入换行字符的转义序列的第一行。
---
title: "数学错误 M6111 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: M6111
dev_langs: C++
helpviewer_keywords: M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 204df0df4855fd2628a96ac326dd39c0d65151e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="math-error-m6111"></a>数学错误 M6111
堆栈下溢  
  
 浮点运算导致堆栈下溢 8087/287/387 协处理器或仿真程序上。  
  
 此错误通常导致通过调用`long double`不返回值的函数。 例如，以下时，将生成此错误编译和运行：  
  
```  
long double ld() {};  
main ()  
{  
  ld();  
}  
```  
  
 程序终止，退出代码 139。
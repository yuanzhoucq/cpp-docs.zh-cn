---
title: 数学错误 M6111 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6111
dev_langs:
- C++
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b03937ed442b169b960d573b44c0eb6ebca9660
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317991"
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
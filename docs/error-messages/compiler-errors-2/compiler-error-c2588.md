---
title: 编译器错误 C2588 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2588
dev_langs:
- C++
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67eb6362ff55e09b05349d10fcdc2377d8ff2996
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231665"
---
# <a name="compiler-error-c2588"></a>编译器错误 C2588
:: ~ 标识符： 非法的全局析构函数  
  
 类、 结构或联合以外为内容定义了析构函数。 这是不允许的。  
  
 此错误可能引起缺少类、 结构或联合名称在范围解析左侧 (`::`) 运算符。  
  
 下面的示例生成 C2588:  
  
```  
// C2588.cpp  
~F();   // C2588  
```
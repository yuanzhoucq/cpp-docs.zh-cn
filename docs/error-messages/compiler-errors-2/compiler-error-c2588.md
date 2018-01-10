---
title: "编译器错误 C2588 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2588
dev_langs: C++
helpviewer_keywords: C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 807574f0f94f989726ca19d3260b9668f6c84055
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
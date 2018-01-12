---
title: "编译器警告 （等级 1） C4392 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4392
dev_langs: C++
helpviewer_keywords: C4392
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7c33a88ae9dda253192fc6ed4616da52ef7c58c1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4392"></a>编译器警告（等级 1）C4392
签名： 内部函数的参数数目不正确预期 number 自变量  
  
 编译器内部函数的函数声明具有错误的参数数量。 生成的图像可能无法正常运行。  
  
 若要解决此警告，请更正声明，或删除该声明，只需 #include 相应的标头文件。  
  
 下面的示例生成 C4392:  
  
```  
// C4392.cpp  
// compile with: /W1  
// processor: x86  
// uncomment the following line and delete the line that  
// generated the warning to resolve  
// #include "xmmintrin.h"  
  
#ifdef  __cplusplus  
extern "C" {  
#endif  
  
extern void _mm_stream_pd(double *dp);   // C4392  
  
#ifdef  __cplusplus  
}  
#endif  
  
int main()  
{  
}  
```
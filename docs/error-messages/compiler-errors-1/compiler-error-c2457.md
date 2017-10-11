---
title: "编译器错误 C2457 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2457
dev_langs:
- C++
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: fd5d73850839c73ea6260165151415115251a59e
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2457"></a>编译器错误 C2457
macro： 预定义的宏不能出现在函数体外部  
  
 您尝试使用预定义的宏，如[__FUNCTION\_\_](../../preprocessor/predefined-macros.md)，在全局空间中。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2457:  
  
```  
// C2457.cpp  
#include <stdio.h>  
  
__FUNCTION__;   // C2457, cannot be global  
  
int main()   
{  
    printf_s("\n%s",__FUNCTION__);   // OK  
}  
```

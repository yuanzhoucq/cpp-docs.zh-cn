---
title: "编译器警告 （等级 4） C4937 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4937
dev_langs: C++
helpviewer_keywords: C4937
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c054051db1b7c765dd2b144b8bd3426593896a91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4937"></a>编译器警告（等级 4）C4937
“text1”和“text2”作为“directive”的参数时不可区分  
  
 由于编译器处理指令的参数的方式不同，无法区分对编译器具有意义的名称，如具有多文本表现形式（单下划线或双下划线形式）的关键字。  
  
 此类字符串的示例包括 __cdecl 和\__forceinline。  请注意，在 /Za 下，仅双下划线形式有效。  
  
 下面的示例生成 C4937：  
  
```  
// C4937.cpp  
// compile with: /openmp /W4  
#include "omp.h"  
int main() {  
   #pragma omp critical ( __leave )   // C4937  
   ;  
  
   // OK  
   #pragma omp critical ( leave )  
   ;  
}  
```
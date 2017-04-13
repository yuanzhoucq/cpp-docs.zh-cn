---
title: "编译器错误 C2099 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2099
dev_langs:
- C++
helpviewer_keywords:
- C2099
ms.assetid: 30e151ee-d458-4901-b0c0-d45054a913f5
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 74fdc75470600c29029c52e38ab2073e484dbde6
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2099"></a>编译器错误 C2099
初始值设定项不是常量  
  
 此错误仅由 C 编译器发出，并仅发生在非自动变量上。  编译器在启动程序时初始化非自动变量，并且初始化的值必须是常数。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2099。  
  
```  
// C2099.c  
int j;  
int *p;  
j = *p;   // C2099 *p is not a constant  
```  
  
## <a name="example"></a>示例  
 因为编译器不能执行常数合并下对表达式也可能发生 C2099 **/fp: strict**由于浮点精度环境设置 (请参阅[_controlfp_s](../../c-runtime-library/reference/controlfp-s.md)有关详细信息) 可能不同于运行时编译。  
  
 当常数折叠失败时，编译器将调用动态初始化，而这在 C 中是不被允许的。  
  
 若要解决此错误，请将模块编译为 .cpp 文件或简化表达式。  
  
 有关详细信息，请参阅 [/fp（指定浮点行为）](../../build/reference/fp-specify-floating-point-behavior.md)。  
  
 下面的示例生成 C2099。  
  
```  
// C2099_2.c  
// compile with: /fp:strict /c  
float X = 2.0 - 1.0;   // C2099  
float X2 = 1.0;   // OK  
```

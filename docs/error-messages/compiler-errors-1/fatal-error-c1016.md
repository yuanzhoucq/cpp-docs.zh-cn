---
title: "错误 C1016 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1016
dev_langs:
- C++
helpviewer_keywords:
- C1016
ms.assetid: 33f45c3e-2d8f-43ad-a445-c412d1d54ce1
caps.latest.revision: 9
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
ms.openlocfilehash: b7f9a620f3df21a737736fce943ee750c7171387
ms.lasthandoff: 04/12/2017

---
# <a name="fatal-error-c1016"></a>错误 C1016
\#ifdef 预期标识符 #ifndef 应输入标识符  
  
 条件编译指令 ([#ifdef](../../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)或`#ifndef`) 具有要计算的标识符。 若要解决此错误，请指定标识符。  
  
 下面的示例生成 C1016：  
  
```  
// C1016.cpp  
#ifdef   // C1016  
#define FC1016  
#endif  
  
int main() {}  
```  
  
 可能的解决方法：  
  
```  
// C1016b.cpp  
#ifdef X  
#define FC1016  
#endif  
  
int main() {}  
```

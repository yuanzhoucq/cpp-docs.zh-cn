---
title: "编译器警告 （等级 1） C4794 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4794
dev_langs:
- C++
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
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
ms.openlocfilehash: 8f73e3da504960f737f175fff4c9d7b07084833a
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4794"></a>编译器警告（等级 1）C4794
线程本地存储区变量“variable”的段由“section name”改为“.tls$”  
  
 你使用[#pragma data_seg](../../preprocessor/data-seg.md)未以.tls$ 开始的节中放置 tls 变量。  
  
 .Tls$*x*节将出现在对象文件其中[__declspec （thread)](../../cpp/thread.md)定义变量。 EXE 或 DLL 中的 .tls 节将从这些节中产生。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4794：  
  
```  
// C4794.cpp  
// compile with: /W1 /c  
#pragma data_seg(".someseg")  
__declspec(thread) int i;   // C4794  
  
// OK  
#pragma data_seg(".tls$9")  
__declspec(thread) int j;  
```

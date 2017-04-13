---
title: "编译器警告 （等级 1） C4920 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4920
dev_langs:
- C++
helpviewer_keywords:
- C4920
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
caps.latest.revision: 6
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
ms.openlocfilehash: e03b1d14116c6d56774c213738581bfca448cfd1
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4920"></a>编译器警告（等级 1）C4920
enum enum member member=value 在 enum enum 中被视为 member=value  
  
 如果传递到 #import 的 .tlb 具有在两个或更多的枚举中定义的相同符号，则此警告指示后续的相同符号被忽略，且会在 .tlh 文件中被注释掉。  
  
 假定 .tlb 包含：  
  
```  
library MyLib  
{  
    typedef enum {  
        enumMember = 512  
    } AProblem;  
  
    typedef enum {  
        enumMember = 1024  
    } BProblem;  
};  
```  
  
 以下示例生成 C4920，  
  
```  
// C4920.cpp  
// compile with: /W1  
#import "t4920.tlb"   // C4920  
  
int main() {  
}  
```

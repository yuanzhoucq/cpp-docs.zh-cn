---
title: "编译器警告 （等级 1） C4399 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4399
dev_langs:
- C++
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 7d7584e318a42530a2a91fee4b428c92bfaf120c
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4399"></a>编译器警告（等级 1）C4399
symbol︰ 不应使用 __declspec （dllimport） 使用 /clr 编译时标记每个进程的符号︰ pure  
  
 **/Clr: pure**编译器选项已弃用 Visual Studio 2015 中。  
  
 本机映像或本机和 CLR 构造与图像中的数据未导入到纯映像。 若要解决此警告，将编译与**/clr** (不**/clr: pure**) 或删除`__declspec(dllimport)`。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4399。  
  
```  
// C4399.cpp  
// compile with: /clr:pure /doc /W1 /c  
__declspec(dllimport) __declspec(process) extern const int i;   // C4399  
```

---
title: "编译器警告 （等级 1） C4627 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4627
dev_langs:
- C++
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
caps.latest.revision: 3
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
ms.openlocfilehash: a435eef7397eb98ca500be1c99e92efcb55c8be6
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4627"></a>编译器警告（等级 1）C4627
\<标识符 1>︰ 在查找预编译标头使用时跳过  
  
 在搜索使用预编译标头的位置，编译器遇到了`#include`指令*\<标识符 1>*包含文件。 编译器将忽略`#include`指令，但发出警告**C4627**如果预编译标头不包含*\<标识符 1>*包含文件。  
  
## <a name="see-also"></a>另请参阅  
 [创建预编译标头文件](../../build/reference/creating-precompiled-header-files.md)

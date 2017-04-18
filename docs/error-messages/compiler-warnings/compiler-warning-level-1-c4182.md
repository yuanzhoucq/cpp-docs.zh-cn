---
title: "编译器警告 （等级 1） C4182 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4182
dev_langs:
- C++
helpviewer_keywords:
- C4182
ms.assetid: 8970f3c6-e2dd-407e-b2ec-964360eb8b43
caps.latest.revision: 7
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
ms.openlocfilehash: 94e014a2eb65173e7022d7d247f073359f10587f
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4182"></a>编译器警告（等级 1）C4182
\#包括嵌套级别为 number 层;可能的无限递归  
  
 由于嵌套的包含文件数量过多，编译器用尽了堆上的空间。 当包含文件包含在另一个包含文件中时，它就是嵌套的。  
  
 此消息仅供参考，并在错误之前[C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)。

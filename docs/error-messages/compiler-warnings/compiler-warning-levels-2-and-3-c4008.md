---
title: "编译器警告 （等级 2 和 3） 等级 C4008 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4008
dev_langs:
- C++
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 0539a36dddf5bed1d7474f6456eb710bb0506ae4
ms.contentlocale: zh-cn
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>编译器警告（等级 2 和等级 3）C4008
“identifier”：“attribute”属性被忽略  
  
 编译器忽略了函数（级别 3 警告）或数据（等级 2 警告）的 `__fastcall`、 **static**或 **inline** 属性。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  `__fastcall`具有数据的属性。  
  
2.  带**inline** 函数的 **static** 或 **inline** 属性。

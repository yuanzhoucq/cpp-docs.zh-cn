---
title: "编译器警告 （等级 4） C4057 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4057
dev_langs:
- C++
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
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
ms.openlocfilehash: 08cacc28c15df5829ead06331178022c76597073
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-4-c4057"></a>编译器警告（等级 4）C4057
“operator”: “identifier1”与“identifier2”在稍微不同的基类型间接寻址上不同  
  
 两个指针表达式引用不同的基类型。 使用表达式时无需转换。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  混合签名和未签名的类型。  
  
2.  混合 **short** 和 **long** 类型。

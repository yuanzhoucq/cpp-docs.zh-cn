---
title: "编译器错误 C2129 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2129
dev_langs:
- C++
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: e2c5bd1b79960f83ef6effeb064375d6b49e8f20
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2129"></a>编译器错误 C2129
静态函数 function 声明但未定义  
  
 对进行的前向引用`static`永远不会定义的函数。  
  
 A`static`必须在文件范围内定义函数。 如果函数在另一个文件中定义的必须将它声明`extern`。

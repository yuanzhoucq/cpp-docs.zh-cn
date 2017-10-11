---
title: "编译器错误 C2818 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2818
dev_langs:
- C++
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 02c1b8e67679e7b8ce69b202c3ddef899439095d
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2818"></a>编译器错误 C2818
重载“operator ->”的应用程序通过类型“type”进行递归  
  
 类成员访问运算符重新定义包含递归`return`语句。 若要重新定义`->`运算符具有递归，你必须将移动到单独的函数调用从运算符的递归例程重写函数。

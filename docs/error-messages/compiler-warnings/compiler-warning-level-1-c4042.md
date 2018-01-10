---
title: "编译器警告 （等级 1） C4042 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4042
dev_langs: C++
helpviewer_keywords: C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0801b3fb34b85a6b07127111b38a35ee826028c4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4042"></a>编译器警告 （等级 1） C4042
identifier： 具有错误的存储类  
  
 指定的存储类不能用于在此上下文中此标识符。 编译器将改为使用默认的存储类：  
  
-   `extern`如果*标识符*是一个函数。  
  
-   **自动**，如果*标识符*是正式参数或局部变量。  
  
-   没有存储类，如果*标识符*是全局变量。  
  
 可以指定存储类而不导致此警告**注册**在参数声明中。  
  
 下面的示例生成 C4042  
  
```  
// C4042.cpp  
// compile with: /W1 /LD  
int func2( __declspec( thread ) int tls_i )    // C4042  
// try the following line instead  
// int func2( int tls_i )  
{  
   return tls_i;  
}  
```
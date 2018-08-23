---
title: 编译器警告 （等级 1） C4042 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4042
dev_langs:
- C++
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bcc4123c18eb9765841a5f6b54446cd064407700
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278380"
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
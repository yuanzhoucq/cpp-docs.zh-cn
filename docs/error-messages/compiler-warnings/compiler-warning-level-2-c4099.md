---
title: 编译器警告 （等级 2） C4099 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4099
dev_langs:
- C++
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afecb3fb2420d27bedf16c81894f224a1119a67b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-2-c4099"></a>编译器警告 （等级 2） C4099
identifier： 首先被使用 objecttype1 现在了解了使用 objecttype2 的类型名称  
  
 作为一种结构声明的对象定义为类，或作为类声明的对象定义为结构。 编译器使用给定定义中的类型。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4099。  
  
```  
// C4099.cpp  
// compile with: /W2 /c  
struct A;  
class A {};   // C4099, use different identifer or use same object type  
```
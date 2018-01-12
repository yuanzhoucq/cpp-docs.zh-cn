---
title: "编译器警告 （等级 2） C4099 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4099
dev_langs: C++
helpviewer_keywords: C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1eb64e859ef40397edeb872cc7f6f228f7ae89e8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
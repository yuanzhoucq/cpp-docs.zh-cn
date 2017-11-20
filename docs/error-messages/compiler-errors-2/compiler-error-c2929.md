---
title: "编译器错误 C2929 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2929
dev_langs: C++
helpviewer_keywords: C2929
ms.assetid: 11134027-6adc-4733-b6bd-b94486bd1933
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1b9b5fe2d73d3c51e2946fc43ef2c5c5cbc5051d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2929"></a>编译器错误 C2929
“identifier”：显式实例化；无法显式强制和取消模板类成员的实例化  
  
 不能在防止标识符实例化的同时对其进行显式实例化。  
  
 下面的示例生成 C2929：  
  
```  
// C2929.cpp  
// compile with: /c  
template<typename T>  
class A {  
public:  
   A() {}  
};  
  
template A<int>::A();  
  
extern template A<int>::A();   // C2929  
```
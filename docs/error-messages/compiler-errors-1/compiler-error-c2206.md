---
title: "编译器错误 C2206 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2206
dev_langs:
- C++
helpviewer_keywords:
- C2206
ms.assetid: d7fba68b-aa28-4885-a9a0-27107358f066
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: f68484c5e28206b29cb4a76d4333c7c2c5fb266e
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2206"></a>编译器错误 C2206
“function”：typedef 不能用于函数定义  
  
 一个 `typedef` 用于定义一种函数类型。  
  
 以下示例生成 C2206：  
  
```  
// C2206.cpp  
typedef int functyp();  
typedef int MyInt;  
functyp func1 {};   // C2206  
int main() {  
   MyInt i = 0;   // OK  
}  
```

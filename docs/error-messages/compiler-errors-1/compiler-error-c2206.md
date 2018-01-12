---
title: "编译器错误 C2206 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2206
dev_langs: C++
helpviewer_keywords: C2206
ms.assetid: d7fba68b-aa28-4885-a9a0-27107358f066
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 172a138f783ef829c1b8e691a1248a9feb2e77dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
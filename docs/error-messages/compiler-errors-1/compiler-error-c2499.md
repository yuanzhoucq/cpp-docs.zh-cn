---
title: "编译器错误 C2499 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2499
dev_langs: C++
helpviewer_keywords: C2499
ms.assetid: b323ff4d-b3c1-4bfd-b052-ae7292d53222
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: aaf3a8cfc59a2bf4d602fc8c194d034704f7bc69
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2499"></a>编译器错误 C2499
class: 类不能是其自己的基类  
  
 你尝试指定要定义用作基类的类。  
  
 下面的示例生成 C2499:  
  
```  
// C2499.cpp  
// compile with: /c  
class CMyClass : public CMyClass {};   // C2499  
class CMyClass{};   // OK  
```
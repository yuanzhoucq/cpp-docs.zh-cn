---
title: "编译器错误 C2010 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2010
dev_langs: C++
helpviewer_keywords: C2010
ms.assetid: 5795ed1d-e206-410b-b7b4-528d125c67b4
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0863e96dfc137cf262fe1aef977c83dc592b798c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2010"></a>编译器错误 C2010
character： 意外宏形参表中  
  
 在宏定义的形参列表中错误地使用了该字符。 删除要解决该错误的字符。  
  
 下面的示例生成 C2010:  
  
```  
// C2010.cpp  
// compile with: /c  
#define mymacro(a|) (2*a)   // C2010  
#define mymacro(a) (2*a)   // OK  
```
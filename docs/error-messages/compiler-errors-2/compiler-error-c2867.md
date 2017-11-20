---
title: "编译器错误 C2867 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2867
dev_langs: C++
helpviewer_keywords: C2867
ms.assetid: 63be26b2-d9ab-4f3d-a8b7-981ce3e4d6b9
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 34fd8669dc210c15488d31a48ffb32198536965d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2867"></a>编译器错误 C2867
identifier： 不是命名空间  
  
 A`using`指令应用于命名空间之外的内容。  
  
 下面的示例生成 C2867:  
  
```  
// C2867.cpp  
// compile with: /c  
namespace N {  
   class X {};  
}  
using namespace N::X;   // C2867  
```
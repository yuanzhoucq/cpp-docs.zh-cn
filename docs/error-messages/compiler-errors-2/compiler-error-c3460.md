---
title: "编译器错误 C3460 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3460
dev_langs: C++
helpviewer_keywords: C3460
ms.assetid: adbf8775-10ca-4654-acdf-58dd765351cd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d0c56650c58849088c030adbe8edf9222cb2ace0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3460"></a>编译器错误 C3460
“type”: 仅可转发用户定义的类型  
  
 有关详细信息，请参阅[类型转发 (C + + /cli CLI)](../../windows/type-forwarding-cpp-cli.md)。  
  
## <a name="example"></a>示例  
 下面的示例创建一个组件。  
  
```  
// C3460.cpp  
// compile with: /LD /clr  
public ref class R {};  
```  
  
## <a name="example"></a>示例  
 下面的示例生成 C3460。  
  
```  
// C3460_b.cpp  
// compile with: /clr /c  
#using "C3460.dll"  
[assembly:TypeForwardedTo(int::typeid)];   // C3460  
[assembly:TypeForwardedTo(R::typeid)];  
```
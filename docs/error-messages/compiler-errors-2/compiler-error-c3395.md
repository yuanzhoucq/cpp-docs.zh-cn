---
title: "编译器错误 C3395 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3395
dev_langs:
- C++
helpviewer_keywords:
- C3395
ms.assetid: 26a9ebc9-ed97-47ce-b436-19aa2bcf6e50
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 93009d77c40535997ecc42ccb715f5fe81d79798
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3395"></a>编译器错误 C3395
function: __declspec （dllexport） 不能应用于具有函数\__clrcall 调用约定  
  
 `__declspec(dllexport)`和[__clrcall](../../cpp/clrcall.md)不兼容。  有关详细信息，请参阅[dllexport、 dllimport](../../cpp/dllexport-dllimport.md)。  
  
 下面的示例生成 C3395:  
  
```  
// C3395.cpp  
// compile with: /clr /c  
  
__declspec(dllexport) void __clrcall Test(){}   // C3395  
void __clrcall Test2(){}   // OK  
__declspec(dllexport) void Test3(){}   // OK  
```

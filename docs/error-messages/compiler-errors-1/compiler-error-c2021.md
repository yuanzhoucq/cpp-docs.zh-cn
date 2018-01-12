---
title: "编译器错误 C2021 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2021
dev_langs: C++
helpviewer_keywords: C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fd62bc02ce871f87101ebd255690e2ff3d81d176
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2021"></a>编译器错误 C2021
应输入指数值而非“character”  
  
 用作浮点常数的指数的字符不是有效的数字。 请务必使用在范围内的指数。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2021:  
  
```  
// C2021.cpp  
float test1=1.175494351E;   // C2021  
```  
  
## <a name="example"></a>示例  
 可能的解决方法：  
  
```  
// C2021b.cpp  
// compile with: /c  
float test2=1.175494351E8;  
```
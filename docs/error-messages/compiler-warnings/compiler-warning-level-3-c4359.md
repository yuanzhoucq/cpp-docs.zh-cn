---
title: "编译器警告 （等级 3） C4359 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4359
dev_langs: C++
helpviewer_keywords: C4359
ms.assetid: d8fe993c-ef82-45a0-a43d-c29f9d1bacdb
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 91af229bdac98dab349c86889665ea4bb49a890b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4359"></a>编译器警告（等级 3）C4359
type： 实际对齐方式 (8) 大于 __declspec(align()) 中指定的值  
  
 指定类型的对齐方式小于某个数据成员的类型的对齐方式。  有关详细信息，请参阅[对齐](../../cpp/align-cpp.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4359。  
  
```  
// C4359.cpp  
// compile with: /W3 /c  
struct __declspec(align(8)) C8 { __int64 i; };  
struct __declspec(align(4)) C4  { C8 m8; };   // C4359  
struct __declspec(align(8)) C8_b  { C8 m8; };   // OK  
struct __declspec(align(16)) C16  { C8 m8; };   // OK  
```
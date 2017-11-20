---
title: "编译器警告 （等级 4） C4221 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4221
dev_langs: C++
helpviewer_keywords: C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cb797b4efce63f3fd8d0b19226611809dd2a5d3c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4221"></a>编译器警告（等级 4）C4221
使用的非标准扩展: identifier： 无法使用自动变量的地址初始化  
  
 使用默认的 Microsoft 扩展 (/Ze) 中，您可以初始化聚合类型 (**数组**， `struct`，或**联合**) 使用本地 （自动） 变量的地址。  
  
## <a name="example"></a>示例  
  
```  
// C4221.c  
// compile with: /W4  
struct S  
{  
   int *i;  
};  
  
void func()  
{  
   int j;  
   struct S s1 = { &j };   // C4221  
}  
  
int main()  
{  
}  
```  
  
 此类初始化操作是在 ANSI 兼容性无效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。
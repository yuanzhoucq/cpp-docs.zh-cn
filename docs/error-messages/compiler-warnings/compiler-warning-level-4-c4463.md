---
title: "编译器警告 （等级 4） C4463 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4463
dev_langs: C++
helpviewer_keywords: C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1bc76019182c376decdd8658defb64dbf90dcfaa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4463"></a>编译器警告 （等级 4） C4463  
  
> 溢出;分配*值*到只包含中的值的位域*low_value*到*high_value*  
  
分配*值*位域所能容纳的值的范围之外。 有符号的位域类型使用高顺序位表示符号，因此，如果 *n* 是有符号的位域是-2 位字段大小，范围<sup>n-1</sup>为 2<sup>n-1</sup>-1，而无符号的位字段具有一个从 0 到 2 范围<sup>n</sup>-1。  
  
## <a name="example"></a>示例  
  
此示例将生成 C4463，因为它尝试分配给类型的位字段的值为 3`int`大小为 2，它具有一个从-2 到 1 范围。  
  
若要解决此问题，可以更改为允许的范围中的一些东西所赋的值。 如果位字段旨在在范围从 0 到 3 中保存无符号的值，你可以更改的声明类型`unsigned`。 如果字段旨在在范围-4 到 3 中保存值，然后可以将位字段大小更改为 3。  
  
```cpp  
// C4463_overflow.cpp
// compile with: cl /W4 /EHsc C4463_overflow.cpp
struct S { 
    int x : 2; // int type treats high-order bit as sign
}; 

int main() { 
    S s; 
    s.x = 3; // warning C4463: overflow; assigning 3 
    // to bit-field that can only hold values from -2 to 1 
    // To fix, change assigned value to fit in range,
    // increase size of bitfield, and/or change base type 
    // to unsigned.
} 
```  

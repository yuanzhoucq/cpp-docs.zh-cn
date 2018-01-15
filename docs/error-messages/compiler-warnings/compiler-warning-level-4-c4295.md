---
title: "编译器警告 （等级 4） C4295 |Microsoft 文档"
ms.custom: 
ms.date: 1/09/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4295
dev_langs: C++
helpviewer_keywords: C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 56ffdce8c2790a3944a8f79753177bc80e249778
ms.sourcegitcommit: bc086a7acbe2d9fd77d115f269cc2a0dbeeb5b88
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2018
---
# <a name="compiler-warning-level-4-c4295"></a>编译器警告（等级 4）C4295
  
> *数组*： 数组是太小，无法包括终止 null 字符  
  
已初始化数组，但数组中的最后一个字符不为 null;访问作为字符串数组可能产生意外的结果。  
  
## <a name="example"></a>示例  
  
下面的示例生成 C4295。 若要解决此问题，你可以声明数组大小更大，以保存终止 null 的初始值设定项字符串，或者也可以使用数组初始值设定项列表进行的意图更明显，这是数组的`char`，不以 null 结尾的字符串。  
  
```C  
// C4295.c
// compile with: /W4


int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```

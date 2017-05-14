---
title: "编译器警告 （等级 4） C4295 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4295
dev_langs:
- C++
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: b831b8e7b838ef25679d49a132c66d4b378fdcd7
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---
# <a name="compiler-warning-level-4-c4295"></a>编译器警告（等级 4）C4295
  
> *数组*︰ 数组是太小，无法包括终止 null 字符  
  
 已初始化数组，但数组中的最后一个字符不为 null;访问数组可能产生意外的结果。  
  
## <a name="example"></a>示例  
  
 下面的示例生成 C4295。 若要解决此问题，你可以声明数组大小更大，以保存终止 null 从初始值设定项。  
  
```C  
// C4295.c  
// compile with: /W4  
  
int main() {  
   char a[3] = "abc";   // C4295  
}  
```

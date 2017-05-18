---
title: "编译器警告 （等级 3） C4191 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4191
dev_langs:
- C++
helpviewer_keywords:
- C4191
ms.assetid: 576d3bc6-95b7-448a-af31-5d798452df09
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 5cdd66e6318867a7f4df8ff70b6440ae6e7bfa3a
ms.contentlocale: zh-cn
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-3-c4191"></a>编译器警告（等级 3）C4191
“operator/operation”：从“type of expression”到“type required”的不安全转换  
  
 涉及函数指针的几个操作被视为不安全：  
  
-   具有不同调用约定的函数类型。  
  
-   具有不同返回约定的函数类型。  
  
-   具有不同的大小、类型类别或分类的参数或返回类型。  
  
-   不同的参数列表长度（在 `__cdecl`上，仅在从较长列表到较短列表的强制转换中，即使较短的列表为 varargs）。  
  
-   指向数据的指针 (而不**void\***) 的函数指针作为别名。  
  
-   任何其他将在 `reinterpret_cast`上产生错误或警告的类型差异。  
  
 通过结果指针调用此函数可能会导致程序故障。  
  
 默认情况下，此警告处于关闭状态。 请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)有关详细信息。  
  
 以下示例生成 C4191：  
  
```  
// C4191.cpp  
// compile with: /W3 /clr  
#pragma warning(default: 4191)  
  
void __clrcall f1() { }  
void __cdecl   f2() { }  
  
typedef void (__clrcall * fnptr1)();  
typedef void (__cdecl   * fnptr2)();  
  
int main() {  
   fnptr1 fp1 = static_cast<fnptr1>(&f1);  
   fnptr2 fp2 = (fnptr2) &f2;  
  
   fnptr1 fp3 = (fnptr1) &f2;   // C4191  
   fnptr2 fp4 = (fnptr2) &f1;   // C4191  
};  
```

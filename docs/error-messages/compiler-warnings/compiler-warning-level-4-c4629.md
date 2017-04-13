---
title: "编译器警告 （等级 4） C4629 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4629
dev_langs:
- C++
helpviewer_keywords:
- C4629
ms.assetid: 158cde12-bae5-4d43-b575-b52b35aaa0b9
caps.latest.revision: 7
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
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: d43d9be531611c40595d56a07f8a8a007cc2bf4b
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-4-c4629"></a>编译器警告（等级 4）C4629
使用了有向图，字符序列“digraph”解释为标记“char”（如果这不是你想要的，请在这两个字符之间插入一个空格）  
  
 下[/Za](../../build/reference/za-ze-disable-language-extensions.md)，编译器会发出警告，这是当它检测到二合字母。  
  
 以下示例生成 C4629：  
  
```  
// C4629.cpp  
// compile with: /Za /W4  
int main()  
<%   // C4629 <% digraph for {  
}  
```

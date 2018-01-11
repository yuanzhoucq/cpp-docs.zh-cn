---
title: "编译器警告 （等级 4） C4629 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4629
dev_langs: C++
helpviewer_keywords: C4629
ms.assetid: 158cde12-bae5-4d43-b575-b52b35aaa0b9
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2d07d2d105c82d1175a9c7cde0326732f0677f35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4629"></a>编译器警告（等级 4）C4629
使用了有向图，字符序列“digraph”解释为标记“char”（如果这不是你想要的，请在这两个字符之间插入一个空格）  
  
 在 [/Za](../../build/reference/za-ze-disable-language-extensions.md)下，当编译器检测到有向图时会发出警告。  
  
 以下示例生成 C4629：  
  
```  
// C4629.cpp  
// compile with: /Za /W4  
int main()  
<%   // C4629 <% digraph for {  
}  
```
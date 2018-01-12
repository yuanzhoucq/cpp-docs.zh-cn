---
title: "编译器错误 C2289 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2289
dev_langs: C++
helpviewer_keywords: C2289
ms.assetid: cb41a29e-1b06-47dc-bfce-8d73bd63a0df
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 86527ef253b460a9ca5b68234d3f10cd87bc36fb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2289"></a>编译器错误 C2289
多次使用同一类型限定符  
  
 类型声明或定义多次使用类型限定符（`const`、 `volatile`、 `signed`或 `unsigned`），从而导致 ANSI 兼容性错误 (**/Za**)。  
  
 下面的示例生成 C2286：  
  
```  
// C2289.cpp  
// compile with: /Za /c  
volatile volatile int i;   // C2289  
volatile int j;   // OK  
```
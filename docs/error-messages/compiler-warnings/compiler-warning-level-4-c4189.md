---
title: "编译器警告 （等级 4） C4189 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4189
dev_langs: C++
helpviewer_keywords: C4189
ms.assetid: 7ad9242c-228e-4054-8244-5e914b618ef3
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 538cd40563890cef2441eeb02f22408c876d7bc2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4189"></a>编译器警告（等级 4）C4189
“identifier”：局部变量已初始化但未引用  
  
 已声明并初始化变量，但未使用。  
  
 下面的示例生成 C4189：  
  
```  
// C4189.cpp  
// compile with: /W4  
int main() {  
   int a = 1;   // C4189, remove declaration to resolve  
}  
```
---
title: "编译器错误 C3744 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3744
dev_langs:
- C++
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
caps.latest.revision: 11
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
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: f6cd256454b51a103d9c4249b050c8c05781bc78
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3744"></a>编译器错误 C3744
对托管事件 __unhook 必须有至少 3 个参数  
  
 [__Unhook](../../cpp/unhook.md)函数必须采用三个参数在 c + + 托管扩展中编译的程序中使用时。  
  
 `__hook`和`__unhook`与 /clr 编程不兼容。 而是使用 + = 和-= 运算符。  
  
 C3744 才可使用已过时的编译器选项连接**/clr:oldSyntax**。  


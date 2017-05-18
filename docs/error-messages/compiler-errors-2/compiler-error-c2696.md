---
title: "编译器错误 C2696 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2696
dev_langs:
- C++
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
caps.latest.revision: 12
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
ms.openlocfilehash: 08b8a7990efbf981aec342b99bbb558fd9fab8d5
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2696"></a>编译器错误 C2696
无法创建临时对象的托管类型 type  
  
对引用`const`托管程序中会导致编译器调用的构造函数，并在堆栈上创建临时对象。 不过，永远不可以在堆栈上创建的托管的类。  
  
C2696 才可使用已过时的编译器选项连接**/clr:oldSyntax**。  


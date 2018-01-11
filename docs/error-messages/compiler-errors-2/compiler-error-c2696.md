---
title: "编译器错误 C2696 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2696
dev_langs: C++
helpviewer_keywords: C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e4d6efbf8dcf10d1608bb1a54b843a49d42cb22a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2696"></a>编译器错误 C2696
无法创建托管类型 type 的临时对象  
  
引用`const`非托管程序中会导致编译器调用的构造函数并在堆栈上创建临时对象。 但是，永远不会可以在堆栈上创建的托管的类。  
  
C2696 才可访问使用过时的编译器选项**/clr:oldSyntax**。  

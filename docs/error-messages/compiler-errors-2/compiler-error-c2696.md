---
title: 编译器错误 C2696 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2696
dev_langs:
- C++
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65ccdd6d2c8c34c360811b80d5a93abe76f5ef8e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235034"
---
# <a name="compiler-error-c2696"></a>编译器错误 C2696
无法创建托管类型 type 的临时对象  
  
引用`const`非托管程序中会导致编译器调用的构造函数并在堆栈上创建临时对象。 但是，永远不会可以在堆栈上创建的托管的类。  
  
C2696 才可访问使用过时的编译器选项 **/clr:oldSyntax**。  

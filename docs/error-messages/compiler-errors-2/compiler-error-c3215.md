---
title: 编译器错误 C3215 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3215
dev_langs:
- C++
helpviewer_keywords:
- C3215
ms.assetid: d0d16007-8885-42e0-b086-2d3a61f348c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a2612441a5a7da7757bce4c2c8005720bf10eafd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33251563"
---
# <a name="compiler-error-c3215"></a>编译器错误 C3215
“type1”: 泛型类型参数已由“type2”进行约束  
  
 已多次指定约束。  
  
 有关泛型的详细信息，请参阅 [Generics](../../windows/generics-cpp-component-extensions.md)。  
  
 下面的示例生成 C3215：  
  
```  
// C3215.cpp  
// compile with: /clr  
interface struct A {};  
  
generic <class T>  
where T : A,A  
ref class C {};   // C3215  
```  
  
 可能的解决方法：  
  
```  
// C3215b.cpp  
// compile with: /clr /c  
interface struct A {};  
  
generic <class T>  
where T : A  
ref class C {};  
```
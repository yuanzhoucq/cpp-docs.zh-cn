---
title: 编译器错误 C3062 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3062
dev_langs:
- C++
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da507511cb5f091d5d9432bbfeb36951e3f43c6f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250561"
---
# <a name="compiler-error-c3062"></a>编译器错误 C3062
'enum': 枚举器需要值，由于基础类型为 type  
  
 你可以指定枚举的基础类型。 但是，某些类型需要你将值分配到每个枚举器。  
  
 枚举的详细信息，请参阅[枚举类](../../windows/enum-class-cpp-component-extensions.md)。  
  
 下面的示例生成 C3062:  
  
```  
// C3062.cpp  
// compile with: /clr  
  
enum class MyEnum : bool { a };   // C3062  
enum class MyEnum2 : bool { a = true};   // OK  
```
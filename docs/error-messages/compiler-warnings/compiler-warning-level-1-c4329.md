---
title: "编译器警告 （等级 1） C4329 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4329
dev_langs: C++
helpviewer_keywords: C4329
ms.assetid: 4316f51a-2c56-4b3f-831e-65d24b83b65c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 35f6936576cd00618603d5bb41e478e69d3f9e7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4329"></a>编译器警告（等级 1）C4329
__declspec(align()) 忽略上枚举  
  
 利用[对齐](../../cpp/align-cpp.md)关键字[__declspec](../../cpp/declspec.md)上不允许使用修饰符`enum`。 下面的示例生成 C4329:  
  
```  
// C4329.cpp  
// compile with: /W1 /LD  
enum __declspec(align(256)) TestEnum {   // C4329  
   TESTVAL1,  
   TESTVAL2,  
   TESTVAL3  
};  
__declspec(align(256)) enum TestEnum1;  
```
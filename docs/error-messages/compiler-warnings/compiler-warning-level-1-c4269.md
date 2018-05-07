---
title: 编译器警告 （等级 1） C4269 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4269
dev_langs:
- C++
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e393c657e12f84d3cadfacd469e35e3472a39d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4269"></a>编译器警告（等级 1）C4269
identifier: const 使用编译器生成默认构造函数初始化的自动数据生成不可靠的结果  
  
 A **const**使用编译器生成的默认构造函数初始化非普通类的自动实例。  
  
## <a name="example"></a>示例  
  
```  
// C4269.cpp  
// compile with: /c /LD /W1  
class X {  
public:  
   int m_data;  
};  
  
void g() {  
   const X x1;   // C4269  
};  
```  
  
 由于在堆栈的初始值上生成类的此实例`m_data`可以是任何内容。 此外，由于它是**const**实例的值`m_data`决不能更改。
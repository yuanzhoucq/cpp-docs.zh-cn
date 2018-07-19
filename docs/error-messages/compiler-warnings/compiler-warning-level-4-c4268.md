---
title: 编译器警告 （等级 4） C4268 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4268
dev_langs:
- C++
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bef62649af39df950c3966ef93dddb6c71ec2fd6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293358"
---
# <a name="compiler-warning-level-4-c4268"></a>编译器警告（等级 4）C4268
identifier: const 全局静态/数据使用编译器生成默认构造函数初始化填充零的对象  
  
 A **const**使用编译器生成的默认构造函数初始化全局或静态的重要类的实例。  
  
## <a name="example"></a>示例  
  
```  
// C4268.cpp  
// compile with: /c /LD /W4  
class X {  
public:  
   int m_data;  
};  
  
const X x1;   // C4268  
```  
  
 类的此实例原样**const**的值`m_data`不能更改。
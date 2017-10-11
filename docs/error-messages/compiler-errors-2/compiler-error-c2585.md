---
title: "编译器错误 C2585 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2585
dev_langs:
- C++
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: cb0720c7fa9cde9a735c4353bb6bf1d8714ff0fd
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2585"></a>编译器错误 C2585
显式转换为 type 不明确  
  
 类型转换可以生成多个结果。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  从基于多个继承的类或结构类型转换。 如果该类型多次继承相同的基类的转换函数或运算符必须使用范围解析 (`::`) 指定哪些继承的类，在转换中使用。  
  
2.  转换运算符和一个构造函数定义了进行相同的转换。

---
title: 编译器错误 C2585 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2585
dev_langs:
- C++
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ab812a4b6621acb28a4df636056598047f5c21e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230156"
---
# <a name="compiler-error-c2585"></a>编译器错误 C2585
显式转换为 type 不明确  
  
 类型转换可以生成多个结果。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  从基于多个继承的类或结构类型转换。 如果该类型多次继承相同的基类的转换函数或运算符必须使用范围解析 (`::`) 指定哪些继承的类，在转换中使用。  
  
2.  转换运算符和一个构造函数定义了进行相同的转换。
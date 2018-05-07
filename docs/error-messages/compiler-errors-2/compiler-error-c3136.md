---
title: 编译器错误 C3136 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3136
dev_langs:
- C++
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f892c7f3d1ca7bf2aebf3ecfe7574182b544fd01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3136"></a>编译器错误 C3136
interface： 只能从另一个 COM 接口继承的 COM 接口，接口不是一个 COM 接口  
  
 应用到接口[接口属性](../../windows/interface-attributes.md)继承自不是一个 COM 接口的接口。 COM 接口最终继承自`IUnknown`。 前面的接口属性是任何接口是一个 COM 接口。  
  
 下面的示例生成 C3136:  
  
```  
// C3136.cpp  
#include "unknwn.h"  
  
__interface A   // C3136  
// try the following line instead  
// _interface A : IUnknown  
{  
   int a();  
};  
  
[object]  
__interface B : A  
{  
   int aa();  
};  
```
---
title: "编译器错误 C3136 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3136
dev_langs:
- C++
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 9e6a8e3c958c6c1293b20451f632910001ef24f2
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

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

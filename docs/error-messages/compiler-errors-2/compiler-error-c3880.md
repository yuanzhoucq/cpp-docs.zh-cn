---
title: "编译器错误 C3880 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3880
dev_langs:
- C++
helpviewer_keywords:
- C3880
ms.assetid: b0e05d1e-32d0-4034-9246-f37d23573ea9
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 5e86108e0ab2608f7f59f160d9f7a849b83ef71a
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3880"></a>编译器错误 C3880
var： 不能为 literal 数据成员  
  
 一种[文本](../../windows/literal-cpp-component-extensions.md)必须是属性，或编译时转换为，以下类型之一：  
  
-   整型  
  
-   string  
  
-   具有整型或基础类型的枚举  
  
 下面的示例生成 C3880:  
  
```  
// C3880.cpp  
// compile with: /clr /c  
ref struct Y1 {  
   literal System::Decimal staticConst1 = 10;   // C3880  
   literal int staticConst2 = 10;   // OK  
};  
```

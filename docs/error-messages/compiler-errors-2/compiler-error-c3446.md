---
title: "编译器错误 C3446 |Microsoft 文档"
ms.custom: 
ms.date: 07/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3446
dev_langs:
- C++
helpviewer_keywords:
- C3445
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 590f9b4012c7a00cb73a61b0d275ff9c5ee9cf9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3446"></a>编译器错误 C3446  
  
>*类*： 默认成员初始值设定项不允许的值类成员  
  
在 Visual Studio 2015 及更早版本中，编译器允许（但会忽略）值类成员的默认成员初始值设定项。 值类的默认初始化始终对成员执行零初始化；不允许使用默认构造函数。 在 Visual Studio 2017 中，默认成员初始值设定项引发编译器错误，如下例所示：

## <a name="example"></a>示例  
 下面的示例生成 C3446 Visual Studio 2017 及更高版本：  
  
```cpp  
// C3446.cpp  
value struct V
{
       int i = 0; // error C3446: 'V::i': a default member initializer  
                  // is not allowed for a member of a value class
       int j {0}; // C3446           
};
```  
  
若要更正错误，删除初始值设定项：  
  
```cpp  
// C3446b.cpp  
value struct V
{
       int i;  
       int j;
};
```  
  

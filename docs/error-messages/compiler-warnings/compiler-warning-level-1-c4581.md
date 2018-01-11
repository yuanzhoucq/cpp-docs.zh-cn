---
title: "编译器警告 （等级 1） C4581 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4581
dev_langs: C++
helpviewer_keywords: C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 59bf4eafe722283f5fced046e845c6b46ca3ce82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4581"></a>编译器警告（等级 1）C4581
已否决的行为:"string1"替换为 string2 进程属性  
  
 此错误可能来自于为 Visual c + + 2005年执行的编译器一致性工作： 查找 Visual c + + 特性的参数。  
  
 在以前版本中，属性值已被接受，无论它们已用引号引起来。 如果值是一个枚举，则它不必须被用引号引起来。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4581。  
  
```  
// C4581.cpp  
// compile with: /c /W1  
#include "unknwn.h"  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI : IUnknown {};  
  
[coclass, uuid(12345678-1111-2222-3333-123456789012), threading("free")]   // C4581  
// try the following line instead  
// [coclass, uuid(12345678-1111-2222-3333-123456789012), threading(free)]  
class CSample : public IMyI {};  
```
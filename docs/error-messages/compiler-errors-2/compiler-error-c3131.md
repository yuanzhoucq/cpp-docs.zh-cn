---
title: 编译器错误 C3131 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3131
dev_langs:
- C++
helpviewer_keywords:
- C3131
ms.assetid: 38f20fac-83c9-4cd9-b7b5-74ca8f650ea6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c722130a0dcf3bea3664e6b0a0ec306d359c8aac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33248683"
---
# <a name="compiler-error-c3131"></a>编译器错误 C3131
项目必须具有 name 属性模块属性  
  
 [模块](../../windows/module-cpp.md)属性必须具有名称参数。  
  
 下面的示例生成 C3131:  
  
```  
// C3131.cpp  
[emitidl];  
[module];   // C3131  
// try the following line instead  
// [module (name="MyLib")];  
  
[public]  
typedef long int LongInt;  
```
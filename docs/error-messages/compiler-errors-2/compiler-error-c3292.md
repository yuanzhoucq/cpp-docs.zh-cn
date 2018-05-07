---
title: 编译器错误 C3292 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3292
dev_langs:
- C++
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55a7f91bb9d47f2675525cf17096deddae30be71
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3292"></a>编译器错误 C3292
cli 命名空间不能重新打开  
  
 cli 命名空间不能在代码中声明。  有关详细信息，请参阅[平台、 default 和 cli 命名空间](../../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 以下示例生成 C3292。  
  
```  
// C3292.cpp  
// compile with: /clr /c  
namespace cli {};   // C3292  
```
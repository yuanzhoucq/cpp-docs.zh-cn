---
title: 编译器错误 C2201 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2201
dev_langs:
- C++
helpviewer_keywords:
- C2201
ms.assetid: ed927659-6e9c-447d-9963-19969ae1e957
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eea410297cdb8deb45c4376f8736234ad8f69699
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170825"
---
# <a name="compiler-error-c2201"></a>编译器错误 C2201
identifier： 必须拥有才能导出/导入的外部链接  
  
 导出的标识符是`static`。  
  
 下面的示例生成 C2286：  
  
```  
// C2201.cpp  
// compile with: /c  
__declspec(dllexport) static void func() {}   // C2201 func() is static  
__declspec(dllexport) void func2() {}   // OK  
```  
  
## <a name="see-also"></a>请参阅  
 [链接的类型](../../cpp/types-of-linkage.md)
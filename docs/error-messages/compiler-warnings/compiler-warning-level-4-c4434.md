---
title: 编译器警告 （等级 4） C4434 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4434
dev_langs:
- C++
helpviewer_keywords:
- C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c639fa1cc89266fd9cc2935d88132ceae225a85e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293408"
---
# <a name="compiler-warning-level-4-c4434"></a>编译器警告（等级 4）C4434
类构造函数必须具有私有可访问性;将更改为私有访问  
  
 C4434 指示编译器更改静态构造函数的可访问性。 静态构造函数必须具有私有可访问性，因为它们仅应由公共语言运行时调用。 有关详细信息，请参阅[静态构造函数](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4434。  
  
```  
// C4434.cpp  
// compile with: /W4 /c /clr  
public ref struct R {  
   static R(){}   // C4434  
};  
```
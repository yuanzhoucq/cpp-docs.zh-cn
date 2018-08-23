---
title: 编译器错误 C3388 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3388
dev_langs:
- C++
helpviewer_keywords:
- C3388
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 481096aa870d7e66df032f4d297c652417a7b487
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256114"
---
# <a name="compiler-error-c3388"></a>编译器错误 C3388
“type”: 不允许作为约束，假定 "ref class" 继续进行分析  
  
 对泛型类型指定了约束，但是未正确地指定约束。 请参阅[泛型类型参数的约束 (C + + /cli CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)有关详细信息。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3388。  
  
```  
// C3388.cpp  
// compile with: /clr /c  
interface class AA {};  
  
generic <class T>  
where T : interface class   // C3388  
ref class C {};  
  
// OK  
generic <class T>  
where T : AA  
ref class D {};  
```
---
title: 编译器错误 C3077 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3077
dev_langs:
- C++
helpviewer_keywords:
- C3077
ms.assetid: d9f3c619-d1e2-4656-81a5-a35a9586a7d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a20b8d650208157550e6a7642c752c607b5e023
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053357"
---
# <a name="compiler-error-c3077"></a>编译器错误 C3077

“finalizer”：终结器只能是引用类型的成员

不能在本机类型或值类型中声明终结器。

有关详细信息，请参阅[析构函数和终结器中如何： 定义和使用类和结构 (C + + CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。

## <a name="example"></a>示例

下面的示例生成 C3077。

```
// C3077.cpp
// compile with: /clr /c
value struct vs {
   !vs(){}   // C3077
};

ref struct rs {
protected:
   !rs(){}   // OK
};
```
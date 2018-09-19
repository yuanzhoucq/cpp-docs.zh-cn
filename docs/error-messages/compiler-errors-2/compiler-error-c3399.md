---
title: 编译器错误 C3399 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3399
dev_langs:
- C++
helpviewer_keywords:
- C3399
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3cae3c038e4af4a58756ad7387472c081bf4c3d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016788"
---
# <a name="compiler-error-c3399"></a>编译器错误 C3399

“type”：创建泛型参数的实例时无法提供变量

当指定 `gcnew()` 约束时，指定约束类型将具有无参数的构造函数。 因此，尝试实例化此类型并传递参数是错误的。

请参阅[泛型类型参数的约束 (C + + CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)有关详细信息。

## <a name="example"></a>示例

以下示例生成 C3399。

```
// C3399.cpp
// compile with: /clr /c
generic <class T>
where T : gcnew()
void f() {
   T t = gcnew T(1);   // C3399
   T t2 = gcnew T();   // OK
}
```
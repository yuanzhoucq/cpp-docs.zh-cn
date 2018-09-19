---
title: 编译器错误 C2785 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2785
dev_langs:
- C++
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cfae8a58d9c42c9ddc3ef7779fc86f7157ba41b0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080852"
---
# <a name="compiler-error-c2785"></a>编译器错误 C2785

declaration1 和 declaration2 具有不同的返回类型

函数模板特殊化的返回类型不同于主函数模板的返回类型。

### <a name="to-correct-this-error"></a>更正此错误

1. 检查一致性的函数模板的所有专用化。

## <a name="example"></a>示例

下面的示例生成 C2785:

```
// C2785.cpp
// compile with: /c
template<class T> void f(T);

template<> int f(int); // C2785
template<> void f(int); // OK
```
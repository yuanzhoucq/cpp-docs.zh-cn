---
title: 编译器错误 C3869 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3869
dev_langs:
- C++
helpviewer_keywords:
- C3869
ms.assetid: 85b2ad72-95c1-4ed6-9761-6ef66c3802b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84b4ce32f6c4916e0e178d488bf725d257f4d887
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020156"
---
# <a name="compiler-error-c3869"></a>C3869

gcnew 约束缺少空参数列表 （）

`gcnew`特殊约束被指定了不含空参数列表。 请参阅[泛型类型参数的约束 (C + + CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)有关详细信息。

## <a name="example"></a>示例

下面的示例生成 C3869。

```
// C3869.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : gcnew   // C3869
// try the following line instead
// where T : gcnew()
ref class List {};
```
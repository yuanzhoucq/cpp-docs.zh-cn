---
title: 编译器错误 C2959 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2959
dev_langs:
- C++
helpviewer_keywords:
- C2959
ms.assetid: d66bb2a8-70c3-4209-a358-b0c47f111a50
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f225dccc917e34fba690064d66cf1cda36219877
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078967"
---
# <a name="compiler-error-c2959"></a>编译器错误 C2959

泛型类或函数可能不是模板的成员

有关详细信息，请参阅[Windows 运行时和托管模板](../../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md)并[泛型](../../windows/generics-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C2959。

```
// C2959.cpp
// compile with: /clr /c
template <class T> ref struct S {
   generic <class U> ref struct GR1;   // C2959
};
```
---
title: 编译器错误 C3467 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3467
dev_langs:
- C++
helpviewer_keywords:
- C3467
ms.assetid: e2b844d0-4920-412f-99fd-cd8051c4aa41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4482aea590b255300a08b5072444b6fabfc5a2eb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026434"
---
# <a name="compiler-error-c3467"></a>编译器错误 C3467

“type”：此类型已被转发

编译器找到了同一类型的多个转发类型声明。 每个类型只允许具有一个声明。

有关详细信息，请参阅[类型转发 (C + + CLI)](../../windows/type-forwarding-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例创建一个组件。

```
// C3467.cpp
// compile with: /LD /clr
public ref class R {};
```

## <a name="example"></a>示例

下面的示例生成 C3467。

```
// C3467_b.cpp
// compile with: /clr /c
#using "C3467.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
[ assembly:TypeForwardedTo(R::typeid) ];   // C3467
```
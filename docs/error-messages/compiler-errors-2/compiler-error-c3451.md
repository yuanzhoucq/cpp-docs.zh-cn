---
title: 编译器错误 C3451 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3451
dev_langs:
- C++
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8685b75684827b4f202317e1df72a8248f1b41dc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085194"
---
# <a name="compiler-error-c3451"></a>编译器错误 C3451

attribute： 不能将非托管的特性 type 应用

C + + 属性不能应用于 CLR 类型。 请参阅[c + + 特性参考](../../windows/cpp-attributes-reference.md)有关详细信息。

有关详细信息，请参阅 [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。

为 Visual c + + 2005年执行的编译器一致性工作可以生成此错误： [uuid](../../windows/uuid-cpp-attributes.md)属性不再允许使用 CLR 编程对用户定义属性。 请改用 <xref:System.Runtime.InteropServices.GuidAttribute>。

## <a name="example"></a>示例

下面的示例生成 C3451。

```
// C3451.cpp
// compile with: /clr /c
using namespace System;
[ attribute(AttributeTargets::All) ]
public ref struct MyAttr {};

[ MyAttr, helpstring("test") ]   // C3451
// try the following line instead
// [ MyAttr ]
public ref struct ABC {};
```
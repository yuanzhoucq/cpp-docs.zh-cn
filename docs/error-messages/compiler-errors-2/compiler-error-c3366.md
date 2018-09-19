---
title: 编译器错误 C3366 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3366
dev_langs:
- C++
helpviewer_keywords:
- C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3638ba2415839c044d9a82d82d0abe8bc2c98e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026499"
---
# <a name="compiler-error-c3366"></a>编译器错误 C3366

variable： 托管的静态数据成员或 WinRTtypes 必须在类定义中定义

尝试在 WinRT 或 .NET 类/接口定义外部引用该类或接口的静态成员。

编译器需要知道类的完整定义（以在一次传递后发出元数据）并要求在类中初始化静态数据成员。

例如，下面的示例生成 C3366，并演示如何修复此错误：

```
// C3366.cpp
// compile with: /clr /c
ref class X {
   public:
   static int i;   // initialize i here to avoid C3366
};

int X::i = 5;      // C3366
```

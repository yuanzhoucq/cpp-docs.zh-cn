---
title: 编译器错误 C3385 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3385
dev_langs:
- C++
helpviewer_keywords:
- C3385
ms.assetid: 5f1838c1-986e-47db-8dbc-e06976b83cf3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac6426e32d5cd9a11d80ddce2cf4203d6a1de0e1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038277"
---
# <a name="compiler-error-c3385"></a>编译器错误 C3385

“class::function”：具有 DllImport 自定义特性的函数不能返回类实例

被定义为位于使用 `DllImport` 特性指定的 .dll 文件中的函数不能返回类的实例。

以下示例生成 C3385：

```
// C3385.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;

struct SomeStruct1 {};

public ref struct Wrap {
   [ DllImport("somedll.dll", CharSet=CharSet::Unicode) ]
   static SomeStruct1 f1([In, Out] SomeStruct1 *pS);   // C3385
};
```

---
title: 编译器错误 C3353 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3353
dev_langs:
- C++
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63316a5a74c3981ec0f68d949eba654f8d6bbfef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110193"
---
# <a name="compiler-error-c3353"></a>编译器错误 C3353

“delegate”: 委托只能从全局函数或者托管或 WinRT 类型的成员函数中创建

与声明的委托[委托](../../windows/delegate-cpp-component-extensions.md)关键字，只能在全局范围内声明。

以下示例生成 C3353：

```
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```
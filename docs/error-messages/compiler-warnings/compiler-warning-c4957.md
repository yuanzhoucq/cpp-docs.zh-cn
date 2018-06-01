---
title: 编译器警告 C4957 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4957
dev_langs:
- C++
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60cf1c03ace94c866b77c5340e2a04a9d8190e4d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705213"
---
# <a name="compiler-warning-c4957"></a>编译器警告 C4957

> *强制转换*： 显式强制转换，从*cast_from*到*cast_to*是不可验证

## <a name="remarks"></a>备注

强制转换会导致不可验证的映像。

某些转换是安全的（例如，触发用户定义的转换的 `static_cast` 和一个 `const_cast`）。 确保 [safe_cast](../../windows/safe-cast-cpp-component-extensions.md) 生成可验证的代码。

有关详细信息，请参阅[纯代码和可验证代码 (C + + /cli CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。

**/Clr: safe**编译器选项是在 Visual Studio 2015 中已过时，并在 Visual Studio 2017 中不支持。

此警告作为错误发出，可通过 [warning](../../preprocessor/warning.md) 杂注或 [/wd](../../build/reference/compiler-option-warning-level.md) 编译器选项禁用该警告。

## <a name="example"></a>示例

以下示例生成 C4957：

```cpp
// C4957.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4957 )
using namespace System;
int main() {
   Object ^ o = "Hello, World!";
   String ^ s = static_cast<String^>(o);   // C4957
   String ^ s2 = safe_cast<String^>(o);   // OK
}
```
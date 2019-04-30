---
title: 编译器警告 C4957
ms.date: 11/04/2016
f1_keywords:
- C4957
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
ms.openlocfilehash: 79a1b516db1508c755693b67ca2e4070095839da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388654"
---
# <a name="compiler-warning-c4957"></a>编译器警告 C4957

> '*cast*： 从显式强制转换*cast_from*to*cast_to*是不可验证

## <a name="remarks"></a>备注

强制转换会导致不可验证的映像。

某些转换是安全的（例如，触发用户定义的转换的 `static_cast` 和一个 `const_cast`）。 确保 [safe_cast](../../extensions/safe-cast-cpp-component-extensions.md) 生成可验证的代码。

有关详细信息，请参阅[纯代码和可验证代码 (C++/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。

**/Clr: safe**编译器选项在 Visual Studio 2015 中弃用并在 Visual Studio 2017 中不受支持。

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
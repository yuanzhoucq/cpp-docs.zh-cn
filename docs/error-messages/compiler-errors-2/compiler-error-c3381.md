---
title: 编译器错误 C3381
ms.date: 11/04/2016
f1_keywords:
- C3381
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
ms.openlocfilehash: ae416d68831d1964c89d938dfcddd364e521195c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440269"
---
# <a name="compiler-error-c3381"></a>编译器错误 C3381

assembly： 程序集访问说明符仅在用 /clr 选项编译的代码中可用

本机类型可以是程序集，外部可见，但只能指定为本机类型中的程序集访问权限 **/clr**编译。

有关详细信息，请参阅[键入可见性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)并[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>示例

下面的示例生成 C3381。

```
// C3381.cpp
// compile with: /c
public class A {};   // C3381
```
---
title: 编译器错误 C3381
ms.date: 11/04/2016
f1_keywords:
- C3381
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
ms.openlocfilehash: eadc9b45b4cd4f2d9b533f387dadd66be8acc963
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749563"
---
# <a name="compiler-error-c3381"></a>编译器错误 C3381

"assembly"：只有在使用/clr 选项编译的代码中才有程序集访问说明符

本机类型在程序集外可见，但你只能在 **/clr**编译中指定本机类型的程序集访问权限。

有关详细信息，请参阅[类型可见性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)和[/Clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>示例

下面的示例生成 C3381。

```cpp
// C3381.cpp
// compile with: /c
public class A {};   // C3381
```

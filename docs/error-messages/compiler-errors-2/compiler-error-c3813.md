---
title: 编译器错误 C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: 88aca16363af22a6671832264889b1a26e43d460
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223364"
---
# <a name="compiler-error-c3813"></a>编译器错误 C3813

属性声明只能在托管类型或 WinRT 类型的定义内出现

[属性](../../dotnet/how-to-use-properties-in-cpp-cli.md)只能在托管类型或 Windows 运行时类型内声明。 本机类型不支持 **`property`** 关键字。

## <a name="example"></a>示例

下面的示例生成 C3813，并演示如何修复此错误：

```cpp
// C3813.cpp
// compile by using: cl /c /clr C3813.cpp
class A
{
   property int Int; // C3813
};

ref class B
{
   property int Int; // OK - declared within managed type
};
```

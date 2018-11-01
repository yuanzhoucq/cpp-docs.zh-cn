---
title: 编译器错误 C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: 302b21d709424cda50abd0247f7b82048511cd73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470585"
---
# <a name="compiler-error-c3813"></a>编译器错误 C3813

属性声明只能在托管类型或 WinRT 类型的定义内出现

一个[属性](../../dotnet/how-to-use-properties-in-cpp-cli.md)只能在托管或 Windows 运行时中声明类型。 本机类型不支持 `property` 关键字。

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
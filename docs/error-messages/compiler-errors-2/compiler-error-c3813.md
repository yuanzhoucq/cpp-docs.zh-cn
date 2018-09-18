---
title: 编译器错误 C3813 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3813
dev_langs:
- C++
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8984feb5b657c26d2137eb9a3c648f1bcf442bf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066266"
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
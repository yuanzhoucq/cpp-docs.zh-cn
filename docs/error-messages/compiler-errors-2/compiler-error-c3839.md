---
title: 编译器错误 C3839
ms.date: 11/04/2016
f1_keywords:
- C3839
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
ms.openlocfilehash: b8382213fbe7cc953dafd9610bfb993ba7837947
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400066"
---
# <a name="compiler-error-c3839"></a>编译器错误 C3839

无法更改托管或 WinRT 类型中的对齐方式

变量的对齐方式在托管或 Windows 运行时类型由 CLR 或 Windows 运行时控制，不能修改与[对齐](../../cpp/align-cpp.md)。

下面的示例生成 C3839：

```
// C3839a.cpp
// compile with: /clr
ref class C
{
public:
   __declspec(align(32)) int m_j; // C3839
};

int main()
{
}
```
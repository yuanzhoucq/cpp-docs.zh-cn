---
title: 编译器错误 C3839
ms.date: 11/04/2016
f1_keywords:
- C3839
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
ms.openlocfilehash: 19a1055a461d76856cc3bccbd9f8af0f0dcff356
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754922"
---
# <a name="compiler-error-c3839"></a>编译器错误 C3839

无法更改托管或 WinRT 类型中的对齐方式

托管或 Windows 运行时类型中的变量对齐由 CLR 或 Windows 运行时控制，不能使用[align](../../cpp/align-cpp.md)进行修改。

下面的示例生成 C3839：

```cpp
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

---
title: 编译器错误 C3624
ms.date: 11/04/2016
f1_keywords:
- C3624
helpviewer_keywords:
- C3624
ms.assetid: eaac6a4f-eb11-4e4d-ab12-124ba995c5cf
ms.openlocfilehash: 3b4f71ed71ddb1b14ed51ccbcd420284ddcc70f6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761915"
---
# <a name="compiler-error-c3624"></a>编译器错误 C3624

"type"：使用此类型需要引用程序集 "assembly"

未指定编译你的代码所需的程序集（引用）;将程序集传递给[#using](../../preprocessor/hash-using-directive-cpp.md)指令。

## <a name="example"></a>示例

下面的示例生成 C3624：

```cpp
// C3624.cpp
// compile with: /clr /c
#using <System.Windows.Forms.dll>

// Uncomment the following 2 lines to resolve.
// #using <System.dll>
// #using <System.Drawing.dll>

using namespace System;

public ref class MyForm : public Windows::Forms::Form {};   // C3624
```

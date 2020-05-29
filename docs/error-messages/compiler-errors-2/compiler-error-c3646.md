---
title: 编译器错误 C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: 13a3ebeb6e7783687abc73cd0dcc018abe827809
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200468"
---
# <a name="compiler-error-c3646"></a>编译器错误 C3646

> "说明符"：未知重写说明符

## <a name="remarks"></a>备注

编译器在预期找到重写说明符的位置找到了一个标记，但编译器无法识别该标记。

例如，如果 **_NOEXCEPT**无法识别的*说明符*，请将其替换为关键字**NOEXCEPT**。

有关详细信息，请参阅[重写说明符](../../extensions/override-specifiers-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3646，并演示如何修复此问题：

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```

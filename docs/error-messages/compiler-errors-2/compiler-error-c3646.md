---
title: 编译器错误 C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: df2e52631ed75cc4a473429ea35e136ed0a88f98
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50606721"
---
# <a name="compiler-error-c3646"></a>编译器错误 C3646

> specifier： 未知重写说明符

## <a name="remarks"></a>备注

编译器在其中它应找到重写说明符，但编译器无法识别标记的位置中找到令牌。

例如，如果无法识别*说明符*是 **_NOEXCEPT**，将其替换为关键字**noexcept**。

有关详细信息，请参阅[重写说明符](../../windows/override-specifiers-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3646，并显示了如何修复此错误：

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```
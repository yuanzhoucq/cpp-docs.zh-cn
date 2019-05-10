---
title: 编译器错误 C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: 04ff1d026c97c56611f8b786d8a7254db711e4a8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385584"
---
# <a name="compiler-error-c3646"></a>编译器错误 C3646

> specifier： 未知重写说明符

## <a name="remarks"></a>备注

编译器在其中它应找到重写说明符，但编译器无法识别标记的位置中找到令牌。

例如，如果无法识别*说明符*是 **_NOEXCEPT**，将其替换为关键字**noexcept**。

有关详细信息，请参阅[重写说明符](../../extensions/override-specifiers-cpp-component-extensions.md)。

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
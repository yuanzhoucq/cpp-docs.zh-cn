---
title: 编译器错误 C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: 90dc3b7a0e1dbc4e0dc6c42ca722ca1db462fca9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558205"
---
# <a name="compiler-error-c3755"></a>编译器错误 C3755

delegate： 不能定义委托

一个[委托 （c + + 组件扩展）](../../windows/delegate-cpp-component-extensions.md)可以声明但未定义。

## <a name="example"></a>示例

下面的示例生成 C3755。

```
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

## <a name="example"></a>示例

如果您尝试创建委托模板，也可能发生 C3755。 下面的示例生成 C3755。

```
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```
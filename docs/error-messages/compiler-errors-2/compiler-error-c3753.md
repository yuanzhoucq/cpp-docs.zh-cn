---
title: 编译器错误 C3753
ms.date: 11/04/2016
f1_keywords:
- C3753
helpviewer_keywords:
- C3753
ms.assetid: a5b99e28-796c-4107-a673-97c2ae3bb2b9
ms.openlocfilehash: 7c9c078e72babc85dc7092b8d6414625e9c0db7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410468"
---
# <a name="compiler-error-c3753"></a>编译器错误 C3753

不允许使用泛型属性

泛型参数列表只能出现在托管的类、 结构或函数。

有关详细信息，请参阅[泛型](../../extensions/generics-cpp-component-extensions.md)并[属性](../../extensions/property-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3753。

```
// C3753.cpp
// compile with: /clr /c
ref struct A {
   generic <typename T>
   property int i;   // C3753 error
};
```
---
title: 编译器错误 C3466
ms.date: 11/04/2016
f1_keywords:
- C3466
helpviewer_keywords:
- C3466
ms.assetid: 69a877d9-a749-474b-bfc3-8d3fd53ba8fd
ms.openlocfilehash: c51dffb1fd8c0a7ef962566635976acca8a3776f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742634"
---
# <a name="compiler-error-c3466"></a>编译器错误 C3466

"type"：泛型类的专用化不能被转发

不能对泛型类的专用化使用类型转发。

有关详细信息，请参阅[类型转发C++（/cli）](../../extensions/type-forwarding-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例创建一个组件。

```cpp
// C3466.cpp
// compile with: /clr /LD
generic<typename T>
public ref class GR {};

public ref class GR2 {};
```

## <a name="example"></a>示例

下面的示例生成 C3466。

```cpp
// C3466_b.cpp
// compile with: /clr /c
#using "C3466.dll"
[assembly:TypeForwardedTo(GR<int>::typeid)];   // C3466
[assembly:TypeForwardedTo(GR2::typeid)];   // OK
```

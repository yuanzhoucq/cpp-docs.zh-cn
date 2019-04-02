---
title: 编译器错误 C3466
ms.date: 11/04/2016
f1_keywords:
- C3466
helpviewer_keywords:
- C3466
ms.assetid: 69a877d9-a749-474b-bfc3-8d3fd53ba8fd
ms.openlocfilehash: 6eae1c44d8dae9118258c83c5919947803f49215
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58771248"
---
# <a name="compiler-error-c3466"></a>编译器错误 C3466

type： 不能转发泛型类的专用化

不能使用类型转发泛型类的专用化。

有关详细信息，请参阅[类型转发 (C + + CLI)](../../extensions/type-forwarding-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例创建一个组件。

```
// C3466.cpp
// compile with: /clr /LD
generic<typename T>
public ref class GR {};

public ref class GR2 {};
```

## <a name="example"></a>示例

下面的示例生成 C3466。

```
// C3466_b.cpp
// compile with: /clr /c
#using "C3466.dll"
[assembly:TypeForwardedTo(GR<int>::typeid)];   // C3466
[assembly:TypeForwardedTo(GR2::typeid)];   // OK
```
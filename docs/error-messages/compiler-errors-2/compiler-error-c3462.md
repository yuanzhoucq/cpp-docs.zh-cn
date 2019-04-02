---
title: 编译器错误 C3462
ms.date: 11/04/2016
f1_keywords:
- C3462
helpviewer_keywords:
- C3462
ms.assetid: 56b75f35-9fad-42d9-a969-eeca5d709bec
ms.openlocfilehash: 020556be73f0bad8bea6836c9ec0dd0b92dd7f39
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781362"
---
# <a name="compiler-error-c3462"></a>编译器错误 C3462

“type”：只有导入的类型才能被转发

TypeForwardedTo 特性必须应用于引用的元数据中的类型。

有关详细信息，请参阅[类型转发 (C + + CLI)](../../extensions/type-forwarding-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例创建一个组件。

```
// C3462.cpp
// compile with: /clr /LD
public ref class R {};
```

## <a name="example"></a>示例

下面的示例生成 C3462。

```
// C3462b.cpp
// compile with: /clr /c
#using "C3462.dll"
ref class N {};
[assembly:TypeForwardedTo(N::typeid)];   // C3462
[assembly:TypeForwardedTo(R::typeid)];
```
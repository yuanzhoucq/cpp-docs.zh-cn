---
title: 编译器警告（等级 4）C4434
ms.date: 11/04/2016
f1_keywords:
- C4434
helpviewer_keywords:
- C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
ms.openlocfilehash: 6a7d760a7d192c7e0a7bd5e16f77efe1a4099c31
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391486"
---
# <a name="compiler-warning-level-4-c4434"></a>编译器警告（等级 4）C4434

类构造函数必须具有私有可访问性;更改为专用访问

C4434 指示编译器更改静态构造函数的可访问性。 静态构造函数必须具有私有可访问性，因为它们仅应由公共语言运行时调用。 有关详细信息，请参阅[静态构造函数](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors)。

## <a name="example"></a>示例

下面的示例生成 C4434。

```
// C4434.cpp
// compile with: /W4 /c /clr
public ref struct R {
   static R(){}   // C4434
};
```
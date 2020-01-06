---
title: 编译器警告（等级 4）C4434
ms.date: 11/04/2016
f1_keywords:
- C4434
helpviewer_keywords:
- C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
ms.openlocfilehash: fccc37ec531768adbe332ddf9fd91ceb708c7185
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990811"
---
# <a name="compiler-warning-level-4-c4434"></a>编译器警告（等级 4）C4434

类构造函数必须具有专用可访问性;更改为专用访问

C4434 指示编译器更改了静态构造函数的可访问性。 静态构造函数必须具有专用可访问性，因为它们只是由公共语言运行时调用。 有关详细信息，请参阅[静态构造函数](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors)。

## <a name="example"></a>示例

下面的示例生成 C4434。

```cpp
// C4434.cpp
// compile with: /W4 /c /clr
public ref struct R {
   static R(){}   // C4434
};
```

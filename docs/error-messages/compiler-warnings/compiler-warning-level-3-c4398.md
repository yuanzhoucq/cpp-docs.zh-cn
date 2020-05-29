---
title: 编译器警告（等级 3）C4398
ms.date: 11/04/2016
f1_keywords:
- C4398
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
ms.openlocfilehash: 041bf9f6bfce17b16f301604bb8706be30095c13
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198661"
---
# <a name="compiler-warning-level-3-c4398"></a>编译器警告（等级 3）C4398

> "*variable*"：每进程全局对象可能无法与多个 appdomain 一起正常工作;考虑使用 __declspec （appdomain）

## <a name="remarks"></a>备注

在本机类型中具有[__clrcall](../../cpp/clrcall.md)调用约定的虚函数会导致创建每个应用程序域 vtable。 当在多个应用程序域中使用此类变量时，可能无法正确更正此类变量。

您可以通过将变量显式标记 `__declspec(appdomain)`来解决此警告。 在 Visual Studio 2017 之前的 Visual Studio 版本中，你可以通过使用 **/clr： pure**进行编译来解决此警告，默认情况下，它会使每个 appdomain 的全局变量成为默认值。 **/Clr： pure**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

有关详细信息，请参阅[appdomain](../../cpp/appdomain.md)和[应用程序域C++和视觉对象](../../dotnet/application-domains-and-visual-cpp.md)。

## <a name="example"></a>示例

下面的示例生成 C4398。

```cpp
// C4398.cpp
// compile with: /clr /W3 /c
struct S {
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall
};

S glob_s;   // C4398
__declspec(appdomain) S glob_s2;   // OK
```

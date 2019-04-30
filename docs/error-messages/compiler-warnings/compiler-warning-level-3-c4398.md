---
title: 编译器警告（等级 3）C4398
ms.date: 11/04/2016
f1_keywords:
- C4398
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
ms.openlocfilehash: 4126a1267b41cdf9c0161c7e85a9057b2a301d77
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401964"
---
# <a name="compiler-warning-level-3-c4398"></a>编译器警告（等级 3）C4398

> '*变量*： 每个进程的全局对象可能无法使用多个 appdomain 正常工作; 请考虑使用 __declspec

## <a name="remarks"></a>备注

使用虚函数[__clrcall](../../cpp/clrcall.md)本机类型中调用约定将导致创建每个应用程序域 vtable。 使用多个应用程序域中时，此类变量可能不正确地更正。

可以通过显式标记变量来解决此警告`__declspec(appdomain)`。 在 Visual Studio 2017 之前的 Visual Studio 版本中，可以通过使用进行编译解决此警告 **/clr: pure**，默认情况下生成每个 appdomain 的全局变量。 **/Clr: pure**编译器选项在 Visual Studio 2015 中弃用并在 Visual Studio 2017 中不受支持。

有关详细信息，请参阅[appdomain](../../cpp/appdomain.md)并[应用程序域和视觉对象C++ ](../../dotnet/application-domains-and-visual-cpp.md)。

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
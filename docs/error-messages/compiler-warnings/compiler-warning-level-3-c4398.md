---
title: 编译器警告 （等级 3） C4398 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4398
dev_langs:
- C++
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c38ade6b75242fdd5144481e3415e914cb6773c5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704609"
---
# <a name="compiler-warning-level-3-c4398"></a>编译器警告（等级 3）C4398

> *变量*： 每个进程的全局对象可能无法与多个 appdomain 进行正常工作; 请考虑使用 __declspec(appdomain)

## <a name="remarks"></a>备注

具有虚拟函数[__clrcall](../../cpp/clrcall.md)本机类型中调用约定将导致创建每个应用程序域 vtable。 在多个应用程序域中使用时，可能无法正确解决此类变量。

通过显式标记变量就可以解决此警告`__declspec(appdomain)`。 在 Visual Studio 2017 之前的 Visual Studio 版本中，则可以通过使用进行编译解决此警告 **/clr: pure**，默认情况下生成每个 appdomain 的全局变量。 **/Clr: pure**编译器选项是在 Visual Studio 2015 中已过时，并在 Visual Studio 2017 中不支持。

有关详细信息，请参阅[appdomain](../../cpp/appdomain.md)和[应用程序域和 Visual c + +](../../dotnet/application-domains-and-visual-cpp.md)。

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
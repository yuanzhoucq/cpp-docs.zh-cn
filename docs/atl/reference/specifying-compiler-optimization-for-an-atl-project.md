---
title: 为 ATL 项目指定编译器优化
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
ms.openlocfilehash: c3b00823cb33be952451c3cc9e370c99140acc3c
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630615"
---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>为 ATL 项目指定编译器优化

默认情况下, [ATL 控件向导](../../atl/reference/atl-control-wizard.md)使用 ATL_NO_VTABLE 宏生成新类, 如下所示:

```
class ATL_NO_VTABLE CProjName
{
...
};
```

然后, ATL 定义 _ATL_NO_VTABLE, 如下所示:

```
#ifdef _ATL_DISABLE_NO_VTABLE
#define ATL_NO_VTABLE
#else
#define ATL_NO_VTABLE __declspec(novtable)
#endif
```

如果未定义 _ATL_DISABLE_NO_VTABLE, 则 ATL_NO_VTABLE 宏将扩展到`declspec(novtable)`。 在`declspec(novtable)`类声明中使用可以防止 vtable 指针在类构造函数和析构函数中进行初始化。 生成项目时, 链接器将消除 vtable 以及 vtable 指向的所有函数。

必须使用 ATL_NO_VTABLE, 因此`declspec(novtable)`只能使用不能直接创建的基类。 不能在项目`declspec(novtable)`中使用与最常派生的类, 因为此类 (通常为[CComObject](../../atl/reference/ccomobject-class.md)、 [CComAggObject](../../atl/reference/ccomaggobject-class.md)或[CComPolyObject](../../atl/reference/ccompolyobject-class.md)) 会初始化项目的 vtable 指针。

不能从使用`declspec(novtable)`的任何对象的构造函数调用虚函数。 应将这些调用移动到[FinalConstruct](ccomobjectrootex-class.md#finalconstruct)方法。

如果不确定是否应使用`declspec(novtable)`修饰符, 可以从任何类定义中删除 ATL_NO_VTABLE 宏, 也可以通过指定

```
#define _ATL_DISABLE_NO_VTABLE
```

在*pch* (Visual Studio 2017 及更早版本中为*stdafx.h* ) 中, 在包含所有其他 ATL 标头文件之前。

## <a name="see-also"></a>请参阅

[ATL 项目向导](../../atl/reference/atl-project-wizard.md)<br/>
[Visual Studio 中的 C++ 项目类型](../../build/reference/visual-cpp-project-types.md)<br/>
[使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[ATL COM 对象基础知识](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[novtable](../../cpp/novtable.md)<br/>
[默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)

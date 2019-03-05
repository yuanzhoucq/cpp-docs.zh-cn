---
title: 指定 ATL 项目的编译器优化
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
ms.openlocfilehash: 6e6fe09aaa0726a39aae8b85cb6581c5d0cd24e1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280012"
---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>指定 ATL 项目的编译器优化

默认情况下[ATL 控件向导](../../atl/reference/atl-control-wizard.md)生成与 ATL_NO_VTABLE 宏的新类，如下所示：

```
class ATL_NO_VTABLE CProjName
{
...
};
```

ATL 然后定义 _ATL_NO_VTABLE，如下所示：

```
#ifdef _ATL_DISABLE_NO_VTABLE
#define ATL_NO_VTABLE
#else
#define ATL_NO_VTABLE __declspec(novtable)
#endif
```

如果未定义 _ATL_DISABLE_NO_VTABLE，ATL_NO_VTABLE 宏会扩展到`declspec(novtable)`。 使用`declspec(novtable)`类中声明会无法 vtable 指针初始化的类构造函数和析构函数中。 生成项目时，链接器可消除 vtable 和 vtable 所指向的所有函数。

必须使用 ATL_NO_VTABLE，并由此`declspec(novtable)`，与仅基类，这些类不是直接可创建对象。 您必须使用`declspec(novtable)`使用派生程度最高的类在项目中，因为此类 (通常[CComObject](../../atl/reference/ccomobject-class.md)， [CComAggObject](../../atl/reference/ccomaggobject-class.md)，或[CComPolyObject](../../atl/reference/ccompolyobject-class.md))初始化你的项目的 vtable 指针。

您不得使用任何对象的构造函数从调用虚函数`declspec(novtable)`。 应将移到这些调用[FinalConstruct](ccomobjectrootex-class.md#finalconstruct)方法。

如果您不确定是否应该使用`declspec(novtable)`修饰符，您可以从任何类定义中，删除 ATL_NO_VTABLE 宏或，可以通过指定全局禁止

```
#define _ATL_DISABLE_NO_VTABLE
```

在 stdafx.h 中之前所有其他 ATL, 标头将包含文件。

## <a name="see-also"></a>请参阅

[ATL 项目向导](../../atl/reference/atl-project-wizard.md)<br/>
[Visual C++ 项目类型](../../ide/visual-cpp-project-types.md)<br/>
[使用应用程序向导创建桌面项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)<br/>
[使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[ATL COM 对象基础知识](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[novtable](../../cpp/novtable.md)<br/>
[默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)

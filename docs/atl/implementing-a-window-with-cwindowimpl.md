---
title: 使用 CWindowImpl 实现窗口
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
ms.openlocfilehash: e5fdbf15ddd7edc69f0667a9b7e08c7c5e531a5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319452"
---
# <a name="implementing-a-window-with-cwindowimpl"></a>使用 CWindowImpl 实现窗口

要实现窗口，从`CWindowImpl`派生类。 在派生类中，声明消息映射和消息处理程序函数。 现在，您可以通过三种不同的方式使用类：

- [基于新的 Windows 类创建窗口](#_atl_creating_a_window_based_on_a_new_windows_class)

- [超级类现有 Windows 类](#_atl_superclassing_an_existing_windows_class)

- [子类现有窗口](#_atl_subclassing_an_existing_window)

## <a name="creating-a-window-based-on-a-new-windows-class"></a><a name="_atl_creating_a_window_based_on_a_new_windows_class"></a>基于新 Windows 类创建窗口

`CWindowImpl`包含[DECLARE_WND_CLASS](reference/window-class-macros.md#declare_wnd_class)宏来声明 Windows 类信息。 此宏实现该`GetWndClassInfo`函数，该函数使用[CWndClassInfo](../atl/reference/cwndclassinfo-class.md)定义新 Windows 类的信息。 调用`CWindowImpl::Create`时，将注册此 Windows 类并创建新窗口。

> [!NOTE]
> `CWindowImpl`将 NULL`DECLARE_WND_CLASS`传递给宏，这意味着 ATL 将生成 Windows 类名称。 要指定自己的名称，请将字符串传递给`CWindowImpl`派生类中的DECLARE_WND_CLASS。

## <a name="example"></a>示例

下面是一个类的示例，该类基于新的 Windows 类实现窗口：

[!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]

要创建窗口，请创建 的`CMyWindow`实例，然后调用`Create`方法。

> [!NOTE]
> 要覆盖默认的 Windows 类信息，`GetWndClassInfo`请通过将`CWndClassInfo`成员设置为适当的值来实现派生类中的方法。

## <a name="superclassing-an-existing-windows-class"></a><a name="_atl_superclassing_an_existing_windows_class"></a>超类现有 Windows 类

[DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass)宏允许您创建一个窗口，用于超类现有 Windows 类。 在`CWindowImpl`派生类中指定此宏。 与任何其他 ATL 窗口一样，消息由消息映射处理。

使用DECLARE_WND_SUPERCLASS时，将注册新的 Windows 类。 此新类将与指定的现有类相同，但会将`CWindowImpl::WindowProc`窗口过程替换为（或使用重写此方法的函数）。

## <a name="example"></a>示例

下面是一个类的示例，该类对标准 Edit 类进行超类类：

[!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]

要创建超类编辑窗口，请创建 的`CMyEdit`实例，然后调用`Create`方法。

## <a name="subclassing-an-existing-window"></a><a name="_atl_subclassing_an_existing_window"></a>对现有窗口进行子分类

要对现有窗口进行子类，从`CWindowImpl`派生类并声明消息映射，如前两种情况。 但是请注意，您不指定任何 Windows 类信息，因为您将对已存在的窗口进行子类。

而不是调用`Create`，`SubclassWindow`调用 并将其句柄传递给要子类的现有窗口。 一旦窗口被子分类，它将使用`CWindowImpl::WindowProc`（或覆盖此方法的函数）将消息定向到消息映射。 要从对象分离子类窗口，请调用`UnsubclassWindow`。 然后，将还原窗口的原始窗口过程。

## <a name="see-also"></a>另请参阅

[实现窗口](../atl/implementing-a-window.md)

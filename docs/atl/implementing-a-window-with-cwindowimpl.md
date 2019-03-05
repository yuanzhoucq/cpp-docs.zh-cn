---
title: 实现与 CWindowImpl 窗口
ms.date: 11/04/2016
f1_keywords:
- CWindowImpl
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
ms.openlocfilehash: 7b1528e331a1431decb3916a06e67f0095615c2d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295846"
---
# <a name="implementing-a-window-with-cwindowimpl"></a>实现与 CWindowImpl 窗口

若要实现一个窗口，从派生类`CWindowImpl`。 在派生类中，声明消息映射和消息处理程序函数。 现在可以通过三种方式使用您的类：

- [创建基于新的 Windows 类的窗口](#_atl_creating_a_window_based_on_a_new_windows_class)

- [超类现有的 Windows 类](#_atl_superclassing_an_existing_windows_class)

- [为现有窗口创建子类](#_atl_subclassing_an_existing_window)

##  <a name="_atl_creating_a_window_based_on_a_new_windows_class"></a> 创建基于新的 Windows 类的窗口

`CWindowImpl` 包含[{2&gt;declare_wnd_class&lt;2](reference/window-class-macros.md#declare_wnd_class)宏声明 Windows 类信息。 此宏实现`GetWndClassInfo`函数，使用[CWndClassInfo](../atl/reference/cwndclassinfo-class.md)定义新的 Windows 类的信息。 当`CWindowImpl::Create`调用时，此 Windows 类注册和创建一个新窗口。

> [!NOTE]
>  `CWindowImpl` 传递到 NULL`DECLARE_WND_CLASS`宏，这意味着 ATL 将生成 Windows 类名称。 若要指定自己的名称，请将字符串传递到中的 {2&gt;declare_wnd_class&lt;2 你`CWindowImpl`-派生的类。

## <a name="example"></a>示例

下面是类的实现基于新的 Windows 类的窗口的示例：

[!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]

若要创建一个窗口，创建的实例`CMyWindow`，然后调用`Create`方法。

> [!NOTE]
>  若要替代默认 Windows 类信息，请实现`GetWndClassInfo`方法通过设置在派生类中的`CWndClassInfo`为适当的值的成员。

##  <a name="_atl_superclassing_an_existing_windows_class"></a> 创建超类现有的 Windows 类

[DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass)宏可用于创建该超类现有 Windows 的一个窗口类。 指定在此宏在`CWindowImpl`-派生的类。 像任何其他 ATL 窗口消息处理的消息映射。

当使用 DECLARE_WND_SUPERCLASS 时，将注册一个新的 Windows 类。 此新类将是与现有的类指定，但将替换具有的窗口过程相同`CWindowImpl::WindowProc`（或带您重写此方法的函数）。

## <a name="example"></a>示例

以下是一个类的示例创建超类标准编辑类：

[!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]

若要创建超类编辑窗口，创建的实例`CMyEdit`，然后调用`Create`方法。

##  <a name="_atl_subclassing_an_existing_window"></a> 子类化现有窗口

为现有窗口的子类，派生的类从`CWindowImpl`并声明消息映射，如前面两种情况中所示。 但请注意，由于将子类现有窗口不会指定任何 Windows 类信息。

而不是调用`Create`，调用`SubclassWindow`并将其传递该句柄到现有窗口想子类。 一旦对窗口子类化，它将使用`CWindowImpl::WindowProc`（或重写此方法的函数） 来将消息定向到的消息映射。 若要分离对象从一个子类化的窗口，请调用`UnsubclassWindow`。 然后将还原窗口的原始窗口过程。

## <a name="see-also"></a>请参阅

[实现窗口](../atl/implementing-a-window.md)

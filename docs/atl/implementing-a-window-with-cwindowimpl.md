---
title: "实现 CWindowImpl 的窗口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CWindowImpl
dev_langs: C++
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b21557fce0735f23e89fe1594a7025170f5f7e7f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="implementing-a-window-with-cwindowimpl"></a>实现 CWindowImpl 的窗口
若要实现一个窗口，从派生类`CWindowImpl`。 在派生类中，声明消息映射和消息处理程序函数。 你现在可以通过三种不同的方式使用您的类：  
  
-   [创建基于新的 Windows 类窗口](#_atl_creating_a_window_based_on_a_new_windows_class)  
  
-   [超类现有 Windows 类](#_atl_superclassing_an_existing_windows_class)  
  
-   [子类化现有窗口](#_atl_subclassing_an_existing_window)  
  
##  <a name="_atl_creating_a_window_based_on_a_new_windows_class"></a>创建基于新的 Windows 类的窗口  
 `CWindowImpl`包含[DECLARE_WND_CLASS](reference/window-class-macros.md#declare_wnd_class)宏声明 Windows 类信息。 此宏实现`GetWndClassInfo`函数，使用[CWndClassInfo](../atl/reference/cwndclassinfo-class.md)定义新的 Windows 类的信息。 当`CWindowImpl::Create`调用时，此窗口类注册和创建一个新窗口。  
  
> [!NOTE]
>  `CWindowImpl`将传递**NULL**到`DECLARE_WND_CLASS`宏，这意味着 ATL 将生成 Windows 类名称。 若要指定您自己的名称，将字符串传递给`DECLARE_WND_CLASS`中你`CWindowImpl`-派生类。  
  
## <a name="example"></a>示例  
 以下是实现基于新的 Windows 类的窗口类的一个示例：  
  
 [!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]  
  
 若要创建一个窗口，创建的实例`CMyWindow`，然后调用**创建**方法。  
  
> [!NOTE]
>  若要重写默认 Windows 类信息，请实现`GetWndClassInfo`通过设置在派生类中的方法`CWndClassInfo`为适当的值的成员。  
  
##  <a name="_atl_superclassing_an_existing_windows_class"></a>创建超类现有 Windows 类  
 [DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass)宏允许你创建该超类现有的 Windows 的窗口类。 指定在此宏你`CWindowImpl`-派生类。 与任何其他 ATL 窗口一样的消息映射来处理消息。  
  
 当你使用`DECLARE_WND_SUPERCLASS`，将注册新的 Windows 类。 此新类将与现有类指定，但将替换具有的窗口过程相同`CWindowImpl::WindowProc`（或与你重写此方法的函数）。  
  
## <a name="example"></a>示例  
 以下是创建超类标准编辑的类的一个示例类：  
  
 [!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]  
  
 若要创建超类编辑窗口，创建的实例`CMyEdit`，然后调用**创建**方法。  
  
##  <a name="_atl_subclassing_an_existing_window"></a>子类化现有的窗口  
 为现有窗口子类化，请从派生类`CWindowImpl`并声明一个消息映射，如下所示前面两种情况。 但是，请注意，由于将子类为现有窗口不会指定任何 Windows 类信息。  
  
 而不是调用**创建**，调用`SubclassWindow`和它将句柄传递到所需子类化的现有窗口。 一旦对窗口子类化，它将使用`CWindowImpl::WindowProc`（或你重写此方法的函数） 来将消息定向到的消息映射。 若要分离子类化的窗口，从你的对象，调用`UnsubclassWindow`。 然后将还原窗口的原始窗口过程。  
  
## <a name="see-also"></a>另请参阅  
 [实现窗口](../atl/implementing-a-window.md)


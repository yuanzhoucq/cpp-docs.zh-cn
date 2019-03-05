---
title: MDI 选项卡式组
ms.date: 11/04/2016
helpviewer_keywords:
- mdi [MFC], tabbed groups
- tabbed grous [MFC]
ms.assetid: 0a464f36-39b7-4e68-8b67-ec175de28377
ms.openlocfilehash: 6b68d1bc06a6827ca94b05fa2760206f424d40fe
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289515"
---
# <a name="mdi-tabbed-groups"></a>MDI 选项卡式组

多文档界面 (MDI) 选项卡式的组功能，多文档界面 (MDI) 应用程序以显示一个或多个选项卡式的窗口 (或组的选项卡式窗口，称为*选项卡式组*) MDI 客户端区域中。 选项卡式窗口可垂直对齐或水平对齐。 如果应用程序承载多个 MDI 选项卡式组，则将用拆分器分隔这些组。

## <a name="features"></a>功能

以下是 MDI 选项卡式组的功能：

- 应用程序可以动态创建选项卡式窗口。

- 应用程序可以水平或垂直对齐选项卡式窗口。

- 将用拆分器分隔选项卡式窗口组。 用户可使用拆分器重设选项卡式组的大小。

- 用户可在各组之间拖动单独的选项卡。

- 用户可拖动单独的选项卡来创建新组。

- 用户可使用快捷菜单移动选项卡或创建新组。

- 应用程序可以保存和加载选项卡式窗口的布局。

- 应用程序可以保存和加载 MDI 文档的列表。

- 应用程序可以访问单独的选项卡式组并修改其参数。

### <a name="using-mdi-tabbed-groups"></a>使用 MDI 选项卡式组

以下是使用 MDI 选项卡式组执行的常见任务：

- 若要启用主框架窗口的 MDI 选项卡式组，请调用[cmdiframewndex:: Enablemditabbedgroups](../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups)。 此方法的第二个参数是 `CMDITabInfo` 类的实例。 您可在调用 `CMDIFrameWndEx::EnableMDITabbedGroups` 之前使用默认参数或修改这些参数。

- 若要在运行时修改 MDI 选项卡式组的属性，请创建或修改 `CMDITabInfo` 对象并再次调用 `CMDIFrameWndEx::EnableMDITabbedGroups`

- 若要获取 MDI 选项卡式窗口的列表，请调用 `CMDIFrameWndEx::GetMDITabGroups`。

- 若要在活动的选项卡式组旁创建新的 MDI 选项卡式组，请调用 `CMDIFrameWndEx::MDITabNewGroup`。

- 若要将输入焦点切换到选项卡式组的上一或下一窗口，请调用 `CMDIFrameWndEx::MDITabMoveToNextGroup`。

- 若要确定窗口是否是 MDI 选项卡式组的成员，请调用 `CMDIFrameWndEx::IsMemberOfMDITabGroup`。

- 若要确定为主框架窗口启用的是 MDI 选项卡还是 MDI 选项卡式组，请调用 `CMDIFrameWndEx::AreMDITabs`。 若要确定是否仅启用了 MDI 选项卡式组，请调用 `CMDIFrameWndEx::IsMDITabbedGroup`。

- 若要在用户单击选项卡或将其拖至其他 MDI 选项卡式组时显示快捷菜单，请重写 `CMDIFrameWndEx::OnShowMDITabContextMenu` 派生类中的 `CMDIFrameWndEx`。 如果您未实现此方法，则应用程序将不会显示快捷菜单。

- 若要将 MDI 选项卡式组的布局保存在应用程序中，请调用 `CMDIFrameWndEx::SaveMDIState`。 若要加载之前保存的 MDI 选项卡式组配置文件，请调用 `CMDIFrameWndEx::LoadMDIState`。 您还可调用这些方法在 MDI 应用程序中加载或保存已打开文档的列表。 有关保存和加载 MDI 状态的详细信息，请参阅[cmdiframewndex:: Loadmdistate](../mfc/reference/cmdiframewndex-class.md#loadmdistate)。

## <a name="see-also"></a>请参阅

[用户界面元素](../mfc/user-interface-elements-mfc.md)<br/>
[CMDIFrameWndEx 类](../mfc/reference/cmdiframewndex-class.md)<br/>
[CMDIChildWndEx 类](../mfc/reference/cmdichildwndex-class.md)<br/>
[CMDITabInfo 类](../mfc/reference/cmditabinfo-class.md)

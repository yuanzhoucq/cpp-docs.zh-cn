---
title: 创建选项卡控件
ms.date: 11/04/2016
f1_keywords:
- TCS_EX_REGISTERDROP
- TCS_EX_FLATSEPARATORS
helpviewer_keywords:
- TCS_EX_REGISTERDROP extended style [MFC]
- tab controls [MFC], creating
- CTabCtrl class [MFC], creating
- TCS_EX_FLATSEPARATORS extended style
ms.assetid: 3a9c2d64-f5f4-41ea-84ab-fceb73c3dbdc
ms.openlocfilehash: 6d5aa6873966ecb4c845f1c503b24c07b6c0c7a3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619610"
---
# <a name="creating-the-tab-control"></a>创建选项卡控件

创建选项卡控件的方式取决于您是在对话框中使用控件，还是在非对话框窗口中创建控件。

### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>直接在对话框中使用 CTabCtrl

1. 在对话框编辑器中，将选项卡控件添加到对话框模板资源。 指定其控件 ID。

1. 使用 "[添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)" 可使用 Control 属性添加类型为[CTabCtrl](reference/ctabctrl-class.md)的成员变量。 您可以使用此成员调用 `CTabCtrl` 成员函数。

1. 对于需要处理的任何选项卡控件通知消息，在对话框类中映射处理程序函数。 有关详细信息，请参阅[将消息映射到函数](reference/mapping-messages-to-functions.md)。

1. 在[OnInitDialog](reference/cdialog-class.md#oninitdialog)中，设置的样式 `CTabCtrl` 。

### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>在非对话框窗口中使用 CTabCtrl

1. 在视图或窗口类中定义控件。

1. 调用控件的[Create](reference/ctabctrl-class.md#create)成员函数，该函数可能在[OnInitialUpdate](reference/cview-class.md#oninitialupdate)中，可能早于父窗口的[OnCreate](reference/cwnd-class.md#oncreate)处理程序函数（如果是控件的子类）。 设置控件的样式。

`CTabCtrl`创建对象后，可以设置或清除以下扩展样式：

- **TCS_EX_FLATSEPARATORS**选项卡控件将在选项卡项之间绘制分隔符。 此扩展样式仅影响具有**TCS_BUTTONS**和**TCS_FLATBUTTONS**样式的选项卡控件。 默认情况下，创建具有**TCS_FLATBUTTONS**样式的选项卡控件将设置此扩展样式。

- **TCS_EX_REGISTERDROP**选项卡控件将生成**TCN_GETOBJECT**通知消息，以便在将对象拖动到控件中的选项卡项上时请求放置目标对象。

    > [!NOTE]
    >  若要接收**TCN_GETOBJECT**通知，必须调用[AFXOLEINIT](reference/ole-initialization.md#afxoleinit)来初始化 OLE 库。

在创建控件后，可以通过分别调用[GetExtendedStyle](reference/ctabctrl-class.md#getextendedstyle)和[SetExtendedStyle](reference/ctabctrl-class.md#setextendedstyle)成员函数来检索和设置这些样式。

例如，将**TCS_EX_FLATSEPARATORS**样式设置为以下代码行：

[!code-cpp[NVC_MFCControlLadenDialog#33](codesnippet/cpp/creating-the-tab-control_1.cpp)]

从**TCS_EX_FLATSEPARATORS** `CTabCtrl` 具有以下代码行的对象中清除 TCS_EX_FLATSEPARATORS 样式：

[!code-cpp[NVC_MFCControlLadenDialog#34](codesnippet/cpp/creating-the-tab-control_2.cpp)]

这将删除在对象的按钮之间出现的分隔符 `CTabCtrl` 。

## <a name="see-also"></a>另请参阅

[使用 CTabCtrl](using-ctabctrl.md)<br/>
[控件](controls-mfc.md)

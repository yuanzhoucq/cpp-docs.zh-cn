---
title: 如何：自定义快速访问工具栏
ms.date: 09/07/2019
helpviewer_keywords:
- quick access toolbar [MFC], customization
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
ms.openlocfilehash: 8b2eb6f7c80c77f69e2bbb65b7bb31a385014c8c
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907780"
---
# <a name="how-to-customize-the-quick-access-toolbar"></a>如何：自定义快速访问工具栏

快速访问工具栏 (QAT) 是一个可自定义的工具栏，其中包含一组显示在“应用程序”按钮旁边或类别选项卡下面的命令。 下图显示了一个典型的快速访问工具栏。

![MFC 功能区快速访问工具栏](../mfc/media/quick_access_toolbar.png "MFC 功能区快速访问工具栏")

若要自定义快速访问工具栏，请在 "**属性**" 窗口中打开它，修改其命令，然后预览功能区控件。

### <a name="to-open-the-quick-access-toolbar-in-the-properties-window"></a>在“属性”窗口中打开快速访问工具栏

1. 在 Visual Studio 的 "**视图**" 菜单上，单击 "**资源视图**"。

1. 在**资源视图**中，双击功能区资源以在设计图面上显示它。

1. 在设计图面上，右键单击 "快速访问工具栏" 菜单，然后单击 "**属性**"。

## <a name="quick-access-toolbar-properties"></a>快速访问工具栏属性

下表定义了快速访问工具栏的属性。

|Property|定义|
|--------------|----------------|
|QAT 位置|在应用程序启动时，指定快速访问工具栏的位置。 位置可以**高于**或**低于**功能区控件。|
|QAT 项|指定可用于快速访问工具栏的命令。|

#### <a name="to-add-or-remove-commands-on-the-quick-access-toolbar"></a>添加或移除快速访问工具栏上的命令

1. 在 "**属性**" 窗口中，单击 " **QAT 项**"，然后单击省略号按钮 **（...）** 。

1. 在 " **QAT 项编辑器**" 对话框中，使用 "**添加**" 和 "**删除**" 按钮来修改快速访问工具栏上命令的列表。

1. 如果希望命令显示在快速访问工具栏和“快速访问工具栏”菜单中，请选择此命令旁边的框。 如果希望命令仅显示在菜单中，请清除此框。

## <a name="previewing-the-ribbon"></a>预览功能区

快速访问工具栏命令不会显示在设计图面上。 若要查看这些命令，则必须预览功能区或运行应用程序。

#### <a name="to-preview-the-ribbon-control"></a>预览功能区控件

- 在**功能区编辑器工具栏**上，单击 "**测试功能区**"。

## <a name="see-also"></a>请参阅

[功能区设计器 (MFC)](../mfc/ribbon-designer-mfc.md)

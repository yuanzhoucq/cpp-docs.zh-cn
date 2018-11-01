---
title: ATL 对话框向导
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.dlg.overview
helpviewer_keywords:
- ATL projects, adding dialog resources
- ATL Dialog Wizard
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
ms.openlocfilehash: 7f868800bb8453ac47ec0f188d6a2970aee7a55f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458043"
---
# <a name="atl-dialog-wizard"></a>ATL 对话框向导

此向导将插入到项目 ATL 对话框框对象，派生自[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)。 一个对话框派生自`CAxDialogImpl`如何托管 ActiveX 控件。

该向导创建对话框资源，默认值**确定**并**取消**按钮。 可以编辑对话框资源，并添加 ActiveX 控件使用[对话框编辑器](../../windows/dialog-editor.md)在资源视图中。

该向导将插入到标头文件[消息映射](../../atl/message-maps-atl.md)单击事件和用于处理默认值的声明。 请参阅[实现对话框](../../atl/implementing-a-dialog-box.md)有关 ATL 对话框的详细信息。

- **短名称**

   设置 ATL 对话框对象的缩写的名称。 所提供的名称确定类名称和文件 （.cpp 和.h） 名称，除非您单独更改这些字段。

- **类**

   设置要创建的类的名称。 此名称基于中提供的名称**短名称**后, 跟 C，这是典型的类名前缀。

- **.h 文件**

   为新项目的类的头文件设置名称。 默认情况下，此名称基于中提供的名称**短名称**。 单击省略号按钮以将该文件名保存至所选择的位置，或追加到某个现有文件的类声明中。 如果选择现有文件，则向导在你单击“完成”之前都不会将其保存至所选位置。

   向导不会覆盖文件。 如果选择现有文件的名称，当你单击“完成”时，向导会询问你是否要将该类声明追加至文件的内容中。 单击“是”，则追加该文件；单击“否”，则返回至向导并指定另一个文件名。

- **.cpp 文件**

   为新项目的类的实现文件设置名称。 默认情况下，此名称基于中提供的名称**短名称**。 单击省略号按钮以将文件名保存到所选位置。 向导在你单击“完成”之前不会将该文件保存到所选位置。

   向导不会覆盖文件。 如果选择现有文件的名称，当你单击“完成”时，向导会询问你是否要将该类实现追加至文件的内容中。 单击“是”，则追加该文件；单击“否”，则返回至向导并指定另一个文件名。

## <a name="see-also"></a>请参阅

[ATL 对话框](../../atl/reference/adding-an-atl-dialog-box.md)


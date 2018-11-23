---
title: 添加事件
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.event.overview
helpviewer_keywords:
- ActiveX controls [C++], adding events to
- MFC ActiveX controls [C++], adding events
- events [C++], ActiveX controls
- add event wizard [C++]
ms.assetid: fe34832a-edfc-4f86-aacb-8df77001873d
ms.openlocfilehash: 1d5a8f5666dd04e00f8a438fdbf00320c37e14f4
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693420"
---
# <a name="add-an-event"></a>添加事件

可以从“类视图”使用[添加事件向导](#add-event-wizard)将事件仅添加到 [MFC ActiveX 控件](../mfc/reference/creating-an-mfc-activex-control.md)项目中的控件类。 如果想要将事件添加到其他项目类型，请使用[属性窗口](/visualstudio/ide/reference/properties-window)中的“事件”按钮。

**将事件添加到 MFC ActiveX 控件项目：**

1. 在“类视图”中，展开项目节点，显示项目中的类。

1. 右键单击项目的控件类。

1. 在快捷菜单上，依次选择“添加”和“添加事件”以显示添加事件向导。

1. 在相应向导框中提供事件信息。

1. 选择“完成”，将事件添加到项目。

## <a name="in-this-section"></a>本节内容

- [添加事件向导](#add-event-wizard)

## <a name="add-event-wizard"></a>添加事件向导

此向导将事件添加到 MFC ActiveX 控件项目。 可以指定自己的事件，自定义典型的常用事件，或者从常用事件列表中进行选择。

- **事件名称**

   设置自动化客户端用来从该类中请求事件的名称。 请输入名称或从列表中选择一个。

- **事件类型**

   指示要添加的事件类型。 仅当从“事件名称”列表中选择时才可用。

   |选项|描述|
   |------------|-----------------|
   |**常用**|指定将对此类实现的常用事件，例如单击按钮。 在 Microsoft 基础类 (MFC) 库中指定常用事件。|
   |**自定义**|指定使用自己的事件实现。|

- **内部名称**

   设置发送该事件的成员函数的名称。 仅适用于自定义事件。 此名称基于“事件名称”。 如果想提供不同于“事件名称”的名称，也可以更改内部名称。

- **参数类型**

   设置“参数名称”的类型。 从列表中选择类型。

- **参数名称**

   设置要通过事件传递的参数名称。 键入名称后，必须选择“添加”才能将其添加到参数列表中。

   选择“添加”后，参数名称随即显示在“参数列表”中。

   > [!NOTE]
   > 如果提供参数名称，且随后在选择“添加”前先选择“完成”，则不会将该参数添加到事件中。 必须找到该方法并手动插入参数。

- **添加**

   将在“参数名称”及其类型中指定的参数添加到“参数列表”。 选择“添加”可向列表添加参数。

- **移除**

   从列表中删除在“参数列表”中选择的参数。

- **参数列表**

   显示当前为该方法添加的所有参数及其类型。 添加参数时，向导更新“参数列表”以显示每个参数及其类型。

---
title: ATL 控件向导
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.overview
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
ms.openlocfilehash: a10c5c358901122dda37b395c1f0fa5cdc30ce30
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321700"
---
# <a name="atl-control-wizard"></a>ATL 控件向导

插入 ATL 项目（或支持 ATL 的 MFC 项目）的 ATL 控件。 您可以使用此向导插入三种控件之一：

- 标准控制

- 复合控制

- DHTML 控件

此外，还可以指定最小控件，从["接口"](../../atl/reference/interfaces-atl-control-wizard.md)列表中删除接口，这些接口作为默认功能提供，供控件在大多数容器中打开。 您可以在向导的 **"接口"** 页中为控件设置所需的控件支持的接口。

## <a name="remarks"></a>备注

此向导生成的注册脚本将在HKEY_CURRENT_USER下注册其 COM 组件，而不是HKEY_LOCAL_MACHINE。 若要修改此行为，请设置 ATL 向导的“为所有用户注册组件”**** 选项。

## <a name="names"></a>名称

命名要添加到项目中的对象、接口和类。 除**短名称**外，所有其他框都可以独立更改。 如果你更改“短名称”**** 的文本，更改会反映在此页中其他所有框的名称中。 如果在 COM 部分中更改**Coclass**名称，则更改将反映在 **"类型"** 框中，但 **"接口**名称"和 **"ProgID"** 不会更改。 此命名行为旨在方便你在开发控件时可轻松识别所有名称。

> [!NOTE]
> **Coclass**仅在非属性化控件上编辑。 如果项目已特性化，便无法编辑“组件类”****。

### <a name="c"></a>C++

提供为了实现对象而创建的 C++ 类的信息。

- **短名称**

   设置对象的缩写名称。 您提供的名称确定类和**Coclass**名称、文件 （。CPP 和 。H） 名称、接口名称和**Type**名称，除非您单独更改这些字段。

- **类**

   设置用于实现对象的类的名称。 此名称以你在“短名称”**** 中提供的名称为依据，跟在典型的类名前缀“C”后面。

- **.h 文件**

   为新项目的类的头文件设置名称。 默认情况下，此名称以你在“短名称”**** 中提供的名称为依据。 单击省略号按钮以将该文件名保存至所选择的位置，或追加到某个现有文件的类声明中。 如果选择现有文件，向导不会将其保存到所选位置，直到单击 **"完成**"。

   向导不会覆盖文件。 如果选择现有文件的名称，当你单击“完成”时，向导会询问你是否要将该类声明追加至文件的内容中****。 单击“是”，则追加该文件；单击“否”，则返回至向导并指定另一个文件名********。

- **.cpp 文件**

   为新项目的类的实现文件设置名称。 默认情况下，此名称以你在“短名称”**** 中提供的名称为依据。 单击省略号按钮以将文件名保存到所选位置。 向导在你单击“完成”之前不会将该文件保存到所选位置****。

   向导不会覆盖文件。 如果选择现有文件的名称，当你单击“完成”时，向导会询问你是否要将该类实现追加至文件的内容中****。 单击“是”，则追加该文件；单击“否”，则返回至向导并指定另一个文件名********。

- **特性化**

   指明对象是否使用特性。 若要将对象添加到特性化 ATL 项目，在选中此选项后便无法更改。 也就是说，只能将特性化对象添加到创建的支持特性的项目中。

   只能将特性化对象添加到使用特性的 ATL 项目中。 如果你对不支持特性的 ATL 项目选中此选项，向导会提示你指定是否要向项目添加特性支持。

   默认情况下，在设置此选项后添加的任何对象都被指定为特性化对象（复选框处于选中状态）。 可以取消选中此框来添加不使用特性的对象。

   有关详细信息，请参阅 [ATL 项目向导的“应用程序设置”](../../atl/reference/application-settings-atl-project-wizard.md)和[特性的基本机制](../../windows/basic-mechanics-of-attributes.md)。

### <a name="com"></a>COM

提供对象的 COM 功能的相关信息。

- **科班**

   设置包含对象支持的接口列表的组件类的名称。

   > [!NOTE]
   > 如果使用属性创建项目，或者在此向导页上指示控件使用属性，则无法更改此选项，因为 ATL 不包括**coclass**属性。

- **接口**

   设置对象的接口的名称。 默认情况下，接口名称以"I"为预写。

- **Type**

   设置注册表中显示的对象说明

- **ProgID**

   设置容器可用来代替对象 CLSID 的名称。 此字段不会自动填充。 如果不手动填充此字段，则控件可能不适用于其他工具。 例如，在 **"插入 ActiveX 控件**"`ProgID`对话框中，没有 生成的 ActiveX 控件不可用。 有关对话框的详细信息，请参阅[插入 ActiveX 控件对话框](../../windows/insert-activex-control-dialog-box.md)。

## <a name="see-also"></a>另请参阅

[ATL 控件](../../atl/reference/adding-an-atl-control.md)<br/>
[向复合控件添加功能](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)

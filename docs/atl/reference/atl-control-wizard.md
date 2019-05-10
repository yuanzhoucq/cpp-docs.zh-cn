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
ms.openlocfilehash: 58c3ebe4c2a15aa3f0d59191c37a7f2422a63ab5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261203"
---
# <a name="atl-control-wizard"></a>ATL 控件向导

插入到 ATL 项目 （或具有 ATL 支持的 MFC 项目） 的 ATL 控件。 此向导可用于插入三种类型的控件之一：

- 标准控件

- 复合控件

- DHTML 控件

此外，您可以指定最小控件中移除从接口[接口](../../atl/reference/interfaces-atl-control-wizard.md)列表，作为控件可以在大多数容器中公开的默认值提供。 可以设置所需的控件中受支持的接口**接口**向导页。

## <a name="remarks"></a>备注

此向导生成的注册脚本将注册而不是 HKEY_LOCAL_MACHINE HKEY_CURRENT_USER 下的其 COM 组件。 若要修改此行为，请设置**的所有用户注册组件**ATL 向导的选项。

## <a name="names"></a>名称

指定的对象、 接口和类添加到你的项目的名称。 除**短名称**，可以独立地更改所有其他框。 如果您更改的文本**短名称**，更改都反映在此页中的所有其他框的名称。 如果您更改**组件类**名称在 COM 部分中，更改将反映在**类型**框中，但**接口**名称并**ProgID**执行操作不是更改。 此命名行为设计以使所有名称轻松地识别为你在开发您的控件。

> [!NOTE]
>  **组件类**是仅非属性化控件上可编辑的。 如果你的项目属性化，则不能编辑**组件类**。

### <a name="c"></a>C++

提供的信息C++为了实现对象创建的类。

- **短名称**

   设置对象的缩写的名称。 你提供的名称确定类和**组件类**命名的文件 (。CPP 和。H） 的名称，接口名称，并**类型**名称，除非您单独更改这些字段。

- **类**

   设置实现对象的类的名称。 此名称基于您在中提供的名称**短名称**后, 跟 C，这是典型的类名前缀。

- **.h 文件**

   为新项目的类的头文件设置名称。 默认情况下，此名称基于您在中提供的名称**短名称**。 单击省略号按钮以将该文件名保存至所选择的位置，或追加到某个现有文件的类声明中。 如果选择一个现有文件，该向导将不将其保存到所选位置直到您单击**完成**。

   向导不会覆盖文件。 如果选择现有文件的名称，当你单击“完成”时，向导会询问你是否要将该类声明追加至文件的内容中。 单击“是”，则追加该文件；单击“否”，则返回至向导并指定另一个文件名。

- **.cpp 文件**

   为新项目的类的实现文件设置名称。 默认情况下，此名称基于您在中提供的名称**短名称**。 单击省略号按钮以将文件名保存到所选位置。 向导在你单击“完成”之前不会将该文件保存到所选位置。

   向导不会覆盖文件。 如果选择现有文件的名称，当你单击“完成”时，向导会询问你是否要将该类实现追加至文件的内容中。 单击“是”，则追加该文件；单击“否”，则返回至向导并指定另一个文件名。

- **特性化**

   指示对象是否使用属性。 如果您向特性化 ATL 项目中添加对象，此选项，并且不能更改。 也就是说，您可以将仅特性化的对象添加到具有属性支持创建的项目。

   可以仅向使用特性的 ATL 项目添加的特性化的对象。 如果选择此选项为不具有支持的属性的 ATL 项目时，向导会提示您指定是否想要添加到项目的属性的支持。

   默认情况下，设置此选项后添加的任何对象都被指定为特性化 （选中复选框）。 您可以清除此框，可以添加不使用属性的对象。

   请参阅[应用程序设置，ATL 项目向导](../../atl/reference/application-settings-atl-project-wizard.md)并[属性的基本结构](../../windows/basic-mechanics-of-attributes.md)有关详细信息。

### <a name="com"></a>COM

为对象提供的 COM 功能有关的信息。

- **组件类**

   设置包含一系列对象支持的接口的组件类的名称。

   > [!NOTE]
   > 如果创建你的项目使用特性，或在此向导页上该控件使用的属性，则不能更改此选项，因为 ATL 不包括**组件类**属性。

- **Interface**

   设置对象的接口的名称。 默认情况下为接口名称前有一个"I"。

- **Type**

   设置会在注册表中的对象说明

- **ProgID**

   设置容器可以使用而不是对象的 CLSID 的名称。 不自动填充此字段。 如果不手动填充此字段，该控件可能不能与其他工具。 例如，无需生成的 ActiveX 控件`ProgID`中不可用**插入 ActiveX 控件**对话框。 有关此对话框的更多信息，请参阅[插入 ActiveX 控件对话框](../../windows/insert-activex-control-dialog-box.md)。

## <a name="see-also"></a>请参阅

[ATL 控件](../../atl/reference/adding-an-atl-control.md)<br/>
[向复合控件添加功能](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[ATL COM 对象基础知识](../../atl/fundamentals-of-atl-com-objects.md)

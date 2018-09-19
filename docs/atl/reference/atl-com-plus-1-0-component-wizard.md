---
title: ATL COM + 1.0 组件向导 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.mts.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding components
- ATL COM+ 1.0 Component Wizard
ms.assetid: 11670681-8671-4122-96a4-2e52f8dadce0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dcf97c08680583dde686c68fb7e26f323e22716e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717895"
---
# <a name="atl-com-10-component-wizard"></a>ATL COM+ 1.0 组件向导

使用此向导将对象添加到项目中，这些支持 COM + 1.0 服务，包括事务。

您可以指定对象是否支持双重接口和自动化。 您还可以指示对错误的信息接口、 增强的对象控件、 事务和异步消息队列的支持。

## <a name="remarks"></a>备注

从 Visual Studio 2008 开始，此向导生成的注册脚本将注册其 COM 组件**HKEY_CURRENT_USER**而不是**HKEY_LOCAL_MACHINE**。 若要修改此行为，请设置**的所有用户注册组件**ATL 向导的选项。

## <a name="names"></a>名称

指定的对象、 接口和类添加到你的项目的名称。 除**短名称**，可以独立于其他编辑所有其他框。 如果您更改的文本**短名称**，更改都反映在此页中的所有其他框的名称。 如果您更改**组件类**名称在 COM 部分中，更改将反映在**类型**并**ProgID**框中，但**接口**名称不会更改。 此命名行为设计以使所有名称轻松地识别为你在开发您的控件。

- **短名称**

   设置对象的缩写的名称。 提供确定的名称`Class`并`Coclass`名称， **.cpp 文件**并 **.h 文件**名称，**接口**命名**类型**名称，并**ProgID**，除非您单独更改这些字段。

- **.h 文件**

   为新项目的类的头文件设置名称。 默认情况下，此名称基于您在中提供的名称**短名称**。 单击省略号按钮以将该文件名保存至所选择的位置，或追加到某个现有文件的类声明中。 如果选择现有文件，则向导在你单击“完成”之前都不会将其保存至所选位置。

   向导不会覆盖文件。 如果选择现有文件的名称，当你单击“完成”时，向导会询问你是否要将该类声明追加至文件的内容中。 单击“是”，则追加该文件；单击“否”，则返回至向导并指定另一个文件名。

- **类**

   设置要创建的类的名称。 此名称基于中提供的名称**短名称**后, 跟 C，这是典型的类名前缀。

- **.cpp 文件**

   为新项目的类的实现文件设置名称。 默认情况下，此名称基于中提供的名称**短名称**。 单击省略号按钮以将文件名保存到所选位置。 向导在你单击“完成”之前不会将该文件保存到所选位置。

   向导不会覆盖文件。 如果选择现有文件的名称，当你单击“完成”时，向导会询问你是否要将该类实现追加至文件的内容中。 单击“是”，则追加该文件；单击“否”，则返回至向导并指定另一个文件名。

- **特性化**

   指示对象是否使用属性。 如果您向特性化 ATL 项目中添加对象，此选项，并且不能更改。 也就是说，您可以将仅特性化的对象添加到具有属性支持创建的项目。

   如果选择此选项为不具有支持的属性的 ATL 项目时，向导会提示您指定是否想要添加到项目的属性的支持。

   设置此选项后添加的任何对象都被指定为特性化默认 （选中复选框）。 您可以清除此框，可以添加不使用属性的对象。

   请参阅[应用程序设置，ATL 项目向导](../../atl/reference/application-settings-atl-project-wizard.md)并[属性的基本结构](../../windows/basic-mechanics-of-attributes.md)有关详细信息。

### <a name="com"></a>COM

为对象提供的 COM 功能有关的信息。

- **组件类**

   设置包含一系列对象支持的接口的组件类的名称。

> [!NOTE]
>  如果创建你的项目使用特性，或在此向导页上的 COM + 1.0 组件使用的属性，则不能更改此选项，因为 ATL 不包括`coclass`属性。

- **Type**

   设置会在注册表中的对象说明

- **Interface**

   设置为对象创建的接口。 此接口包含自定义方法。

- **ProgID**

   设置容器可以使用而不是对象的 CLSID 的名称。

## <a name="see-also"></a>请参阅

[ATL COM + 1.0 组件](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)


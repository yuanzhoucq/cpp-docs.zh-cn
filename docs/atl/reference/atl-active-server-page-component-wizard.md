---
title: ATL Active Server Page 组件向导
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.overview
helpviewer_keywords:
- ASP components, creating in ATL
- ATL Active Server Page Component Wizard
ms.assetid: 5a5cb904-dbbf-44ea-ad3d-2ddd14c1d3c5
ms.openlocfilehash: 80d7eefaa4b12d5aab8970f4b3c81fc644226e07
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50510859"
---
# <a name="atl-active-server-page-component-wizard"></a>ATL Active Server Page 组件向导

此向导将 Active Server Pages (ASP) 组件插入到项目中。 Microsoft Internet 信息服务 (IIS) 使用 ASP 组件作为其增强的 Web 页面开发体系结构的一部分。

通过使用此向导，可以指定组件的线程模型和它聚合的支持。 您还可以指示支持错误信息接口、 连接点和自由线程封送处理。

> [!WARNING]
> 在 Visual Studio 2017 版本 15.9 中，此代码向导已弃用，并将从 Visual Studio 的将来版本中删除。 很少用到此向导。 对 ATL 和 MFC 的常规支持不会受到删除此向导的影响。 如果你想要共享对此弃用的反馈，请完成[此调查](https://www.surveymonkey.com/r/QDWKKCN)。 你的反馈对我们很重要。

## <a name="remarks"></a>备注

从 Visual Studio 2008 开始，此向导生成的注册脚本将注册其 COM 组件**HKEY_CURRENT_USER**而不是**HKEY_LOCAL_MACHINE**。 若要修改此行为，请设置**的所有用户注册组件**ATL 向导的选项。

## <a name="names"></a>名称

指定的对象、 接口和类添加到你的项目的名称。 除**短名称**，可以独立于其他编辑所有其他框。 如果您更改的文本**短名称**，更改都反映在此页中的所有其他框的名称。

如果您更改**组件类**名称在 COM 部分中，更改将反映在**类型**并**ProgID**框中，但**接口**名称不会更改。 此命名行为设计以使所有名称轻松地识别为你在开发您的控件。

### <a name="c"></a>C++

提供为对象创建的 c + + 类的信息。

- **短名称**

   设置对象的根名称。 提供确定的名称`Class`并**Coclass**名称， **.cpp 文件**并 **.h 文件**名称，**接口**名称，**类型**名称，并**ProgID**，除非您单独更改这些字段。

- **.h 文件**

   为新项目的类的头文件设置名称。 默认情况下，此名称基于您在中提供的名称**短名称**。 单击省略号按钮以将该文件名保存至所选择的位置，或追加到某个现有文件的类声明中。 如果选择一个现有文件，该向导将不将其保存到所选位置直到您单击**完成**向导中。

   向导不会覆盖文件。 如果选择现有文件的名称，当你单击“完成”时，向导会询问你是否要将该类声明追加至文件的内容中。 单击“是”，则追加该文件；单击“否”，则返回至向导并指定另一个文件名。

- **类**

   设置要创建的类的名称。 此名称基于您在中提供的名称**短名称**后, 跟 C，这是典型的类名前缀。

- **.cpp 文件**

   为新项目的类的实现文件设置名称。 默认情况下，此名称基于您在中提供的名称**短名称**。 单击省略号按钮以将文件名保存到所选位置。 向导在你单击“完成”之前不会将该文件保存到所选位置。

   向导不会覆盖文件。 如果选择现有文件的名称，当你单击“完成”时，向导会询问你是否要将该类实现追加至文件的内容中。 单击“是”，则追加该文件；单击“否”，则返回至向导并指定另一个文件名。

- **特性化**

   指示对象是否使用属性。 如果您向特性化 ATL 项目中添加对象，此选项，并且不能更改。 也就是说，您可以将仅特性化的对象添加到具有属性支持创建的项目。

   如果选择此选项为不具有支持的属性的 ATL 项目时，向导会提示您指定是否想要添加到项目的属性的支持。

   默认情况下，对于非特性化项目中，设置此选项后添加的任何对象都被指定为特性化 （选中复选框）。 您可以清除此框，可以添加不使用属性的对象。

   请参阅[应用程序设置，ATL 项目向导](../../atl/reference/application-settings-atl-project-wizard.md)并[属性的基本结构](../../windows/basic-mechanics-of-attributes.md)有关详细信息。

### <a name="com"></a>COM

为对象提供的 COM 功能有关的信息。

- **组件类**

   设置包含一系列对象支持的接口的组件类的名称。 如果你的项目或该对象使用的属性，则不能更改此选项，因为 ATL 不包括**组件类**属性。

- **Type**

   设置会在用于 coclass 注册表中的对象说明。

- **Interface**

   设置为对象创建的接口。 此接口包含自定义方法。

- **ProgID**

   设置容器可以使用而不是对象的 CLSID 的名称。

## <a name="see-also"></a>请参阅

[ATL Active Server Page 组件](../../atl/reference/adding-an-atl-active-server-page-component.md)

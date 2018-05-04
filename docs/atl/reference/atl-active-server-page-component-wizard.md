---
title: ATL Active Server Page 组件向导 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.asp.overview
dev_langs:
- C++
helpviewer_keywords:
- ASP components, creating in ATL
- ATL Active Server Page Component Wizard
ms.assetid: 5a5cb904-dbbf-44ea-ad3d-2ddd14c1d3c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d717eefe9c9ee353692d343b88c57469eeb6892
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="atl-active-server-page-component-wizard"></a>ATL Active Server Page 组件向导
此向导将 Active Server Pages (ASP) 组件插入到项目中。 Microsoft Internet 信息服务 (IIS) 使用 ASP 组件作为其增强的网页开发体系结构的一部分。  
  
 通过使用此向导，可以指定组件的线程模型和它聚合的支持。 您还可以指示支持错误信息接口、 连接点和自由线程封送处理。  
  
## <a name="remarks"></a>备注  
 从 Visual Studio 2008 开始，通过此向导生成的注册脚本将注册其 COM 组件**HKEY_CURRENT_USER**而不是**HKEY_LOCAL_MACHINE**。 若要修改此行为，请设置**为所有用户注册组件**ATL 向导的选项。  
  
## <a name="names"></a>名称  
 指定的对象、 接口和类添加到你的项目的名称。 除**短名称**，所有其他框可以相互独立地进行编辑。 如果你更改的文本**短名称**，此更改反映在此页中的所有其他框的名称。  
  
 如果你更改**组件类**名称中 COM 部分中，更改将反映在**类型**和**ProgID**框中，但**接口**名称不会更改。 此命名行为旨在使所有名称轻松地识别为您开发您的控件。  
  
### <a name="c"></a>C++  
 提供信息的对象创建的 c + + 类。  
  
 **短名称**  
 设置对象的根名称。 提供确定的名称`Class`和**组件类**名称， **.cpp 文件**和 **.h 文件**名称，**接口**名称，**类型**名称，与**ProgID**，除非单独更改这些字段。  
  
 **.h 文件**  
 设置新对象的类的头文件的名称。 默认情况下，此名称基于你在中提供的名称**短名称**。 单击省略号按钮，以将文件名称保存到你选择的位置，或者将类声明追加到现有文件。 如果选择现有文件时，向导将不将其保存到所选位置直到你单击**完成**向导中。  
  
 向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类声明是否应追加到文件的内容。 单击**是**要追加文件; 单击**否**返回到向导并指定另一个文件的名称。  
  
 **类**  
 设置要创建的类的名称。 此名称根据你在中提供的名称**短名称**前有一个 c，这是典型的类名前缀。  
  
 **.cpp 文件**  
 设置新对象的类实现文件的名称。 默认情况下，此名称基于你在中提供的名称**短名称**。 单击省略号按钮以将文件名称保存到你选择的位置。 文件不保存到选定的位置，直到您单击**完成**向导中。  
  
 向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类实现是否应追加到文件的内容。 单击**是**要追加文件; 单击**否**返回到向导并指定另一个文件的名称。  
  
 **特性化**  
 指示对象是否使用属性。 如果将对象添加到特性化 ATL 项目中，此选项被选中并且不能更改。 也就是说，你可以将仅特性化的对象添加到具有属性支持创建的项目。  
  
 如果选择此选项为不具有支持的属性的 ATL 项目时，向导会提示你指定是否想要将属性支持添加到项目。  
  
 默认情况下，对于非特性化项目中，设置此选项后添加的任何对象都被指定为特性化 （复选框为选中状态）。 你可以清除此框以添加不使用属性的对象。  
  
 请参阅[应用程序设置，ATL 项目向导](../../atl/reference/application-settings-atl-project-wizard.md)和[特性的基本机制](../../windows/basic-mechanics-of-attributes.md)有关详细信息。  
  
### <a name="com"></a>COM  
 为对象提供的 COM 功能有关的信息。  
  
 **组件类**  
 设置包含的一组对象支持的接口的组件类的名称。 如果你的项目或此对象使用特性，则无法更改此选项，因为 ATL 不包括**组件类**属性。  
  
 **Type**  
 设置会在组件类的注册表中显示的对象说明。  
  
 **Interface**  
 设置为你的对象创建的接口。 此接口包含自定义方法。  
  
 **ProgID**  
 设置容器可以使用而不是对象的 CLSID 的名称。  
  
## <a name="see-also"></a>请参阅  
 [ATL Active Server Page 组件](../../atl/reference/adding-an-atl-active-server-page-component.md)


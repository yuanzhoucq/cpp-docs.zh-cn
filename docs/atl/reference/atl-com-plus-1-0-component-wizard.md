---
title: ATL COM + 1.0 组件向导 |Microsoft 文档
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
ms.openlocfilehash: 19151ca659f7bc3235f84eefb39b640c4856fa43
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361298"
---
# <a name="atl-com-10-component-wizard"></a>ATL COM+ 1.0 组件向导
使用此向导将对象添加到您的项目，支持 COM + 1.0 服务，包括事务。  
  
 你可以指定对象是否支持双重接口和自动化。 您还可以指示对错误信息接口、 控制增强的对象、 事务和异步消息队列支持。  
  
## <a name="remarks"></a>备注  
 从 Visual Studio 2008 开始，通过此向导生成的注册脚本将注册其 COM 组件**HKEY_CURRENT_USER**而不是**HKEY_LOCAL_MACHINE**。 若要修改此行为，请设置**为所有用户注册组件**ATL 向导的选项。  
  
## <a name="names"></a>名称  
 指定的对象、 接口和类添加到你的项目的名称。 除**短名称**，所有其他框可以相互独立地进行编辑。 如果你更改的文本**短名称**，此更改反映在此页中的所有其他框的名称。 如果你更改**组件类**名称中 COM 部分中，更改将反映在**类型**和**ProgID**框中，但**接口**名称不会更改。 此命名行为旨在使所有名称轻松地识别为您开发您的控件。  
  
 **短名称**  
 设置对象的缩写的名称。 提供确定的名称`Class`和`Coclass`名称， **.cpp 文件**和 **.h 文件**名称，**接口**命名**类型**名称，与**ProgID**，除非单独更改这些字段。  
  
 **.h 文件**  
 设置新对象的类的头文件的名称。 默认情况下，此名称基于你在中提供的名称**短名称**。 单击省略号按钮，以将文件名称保存到你选择的位置，或者将类声明追加到现有文件。 如果你选择现有文件，向导将不将其保存到所选位置直到你单击**完成**向导中。  
  
 向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类声明是否应追加到文件的内容。 单击**是**要追加文件; 单击**否**返回到向导并指定另一个文件的名称。  
  
 **类**  
 设置要创建的类的名称。 此名称根据你在中提供的名称**短名称**前有一个 c，这是典型的类名前缀。  
  
 **.cpp 文件**  
 设置新对象的类实现文件的名称。 默认情况下，此名称基于你在中提供的名称**短名称**。 单击省略号按钮以将文件名称保存到你选择的位置。 文件不保存到选定的位置，直到您单击**完成**向导中。  
  
 向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类实现是否应追加到文件的内容。 单击**是**要追加文件; 单击**否**返回到向导并指定另一个文件的名称。  
  
 **特性化**  
 指示对象是否使用属性。 如果将对象添加到特性化 ATL 项目中，此选项被选中并且不能更改。 也就是说，你可以将仅特性化的对象添加到具有属性支持创建的项目。  
  
 如果选择此选项为不具有支持的属性的 ATL 项目时，向导会提示你指定是否想要将属性支持添加到项目。  
  
 设置此选项后添加的任何对象都指定为特性化默认 （选中复选框）。 你可以清除此框以添加不使用属性的对象。  
  
 请参阅[应用程序设置，ATL 项目向导](../../atl/reference/application-settings-atl-project-wizard.md)和[特性的基本机制](../../windows/basic-mechanics-of-attributes.md)有关详细信息。  
  
### <a name="com"></a>COM  
 为对象提供的 COM 功能有关的信息。  
  
 **组件类**  
 设置包含的一组对象支持的接口的组件类的名称。  
  
> [!NOTE]
>  如果你创建项目使用属性，或在此向导页中的 COM + 1.0 组件使用特性，你不能更改此选项，因为 ATL 不包括`coclass`属性。  
  
 **Type**  
 设置会在注册表中显示的对象说明  
  
 **Interface**  
 设置为你的对象创建的接口。 此接口包含自定义方法。  
  
 **ProgID**  
 设置容器可以使用而不是对象的 CLSID 的名称。  
  
## <a name="see-also"></a>请参阅  
 [ATL COM + 1.0 组件](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)


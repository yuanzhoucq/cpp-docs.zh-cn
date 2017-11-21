---
title: "ATL 简单对象向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.simple.overview
dev_langs: C++
helpviewer_keywords:
- ATL projects, adding objects
- ATL Simple Object Wizard
ms.assetid: f7f85741-9aad-4543-a917-a29b996364da
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bfbb97f66065efd0a9ef06de0ff427e893610955
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="atl-simple-object-wizard"></a>ATL 简单对象向导
此向导将最小的 COM 对象插入到项目中。 向导的此页用于指定标识的 c + + 类和你的对象和其 COM 功能文件的名称。  
  
 使用[选项](../../atl/reference/options-atl-simple-object-wizard.md)页的此向导来指定对象的线程模型，其聚合支持，以及它是否支持双重接口和自动化。 您还可以指示支持错误信息接口、 连接点、 Internet Explorer 支持和自由线程封送处理。  
  
## <a name="remarks"></a>备注  
 从 Visual Studio 2008 开始，通过此向导生成的注册脚本将注册其 COM 组件**HKEY_CURRENT_USER**而不是**HKEY_LOCAL_MACHINE**。 若要修改此行为，请设置**为所有用户注册组件**ATL 向导的选项。  
  
## <a name="names"></a>名称  
 指定的对象、 接口和类添加到你的项目的名称。 除**短名称**，所有其他框可以相互独立地进行编辑。 如果你更改的文本**短名称**，此更改反映在此页中的所有其他框的名称。 如果你更改**组件类**名称中 COM 部分中，更改将反映在**类型**和**ProgID**框中，但**接口**名称不会更改。 此命名行为旨在使所有名称轻松地识别为您开发您的控件。  
  
> [!NOTE]
>  **组件类**是在仅非属性化项目上编辑。 如果你的项目特性化，则不能编辑**组件类**。  
  
## <a name="c"></a>C++  
 提供信息的对象创建的 c + + 类。  
  
 **短名称**  
 设置对象的缩写的名称。 提供确定的名称`Class`和**组件类**名称， **.cpp 文件**和**.h 文件**名称，**接口**名称，**类型**名称，与**ProgID**，除非单独更改这些字段。  
  
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
  
 你可以仅向使用特性的 ATL 项目中添加的特性化的对象。 如果选择此选项为不具有支持的属性的 ATL 项目时，向导会提示你指定是否想要将属性支持添加到项目。  
  
 默认情况下，设置此选项后添加的任何对象都被指定为特性化 （复选框为选中状态）。 你可以清除此框以添加不使用属性的对象。  
  
 请参阅[应用程序设置，ATL 项目向导](../../atl/reference/application-settings-atl-project-wizard.md)和[特性的基本机制](../../windows/basic-mechanics-of-attributes.md)有关详细信息。  
  
## <a name="com"></a>COM  
 为对象提供的 COM 功能有关的信息。  
  
 **组件类**  
 设置包含的一组对象支持的接口的组件类的名称。  
  
> [!NOTE]
>  如果你创建项目使用属性，或者如果在此向导页中指示该对象使用特性，则无法更改此选项，因为 ATL 不包括`coclass`属性。  
  
 **类型**  
 设置会在注册表中显示的对象说明  
  
 **Interface**  
 设置为你的对象创建的接口。 此接口包含自定义方法。  
  
 **ProgID**  
 设置容器可以使用而不是对象的 CLSID 的名称。  
  
## <a name="see-also"></a>另请参阅  
 [ATL 简单对象](../../atl/reference/adding-an-atl-simple-object.md)


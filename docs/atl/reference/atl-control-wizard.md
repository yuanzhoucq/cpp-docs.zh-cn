---
title: "ATL 控件向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.control.overview
dev_langs: C++
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5a9167153c2b827e1bc2597e830e9b3c82ee31b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="atl-control-wizard"></a>ATL 控件向导
ATL 项目 （或具有 ATL 支持的 MFC 项目） 插入 ATL 控件。 此向导可用于插入一个三种类型的控件：  
  
-   标准控件  
  
-   复合控件  
  
-   DHTML 控件  
  
 此外，你可以指定最低限度的控制，删除从接口[接口](../../atl/reference/interfaces-atl-control-wizard.md)列表中，作为默认值，用于控制以在大多数容器中公开提供。 你可以设置所需的控件中受支持的接口**接口**向导页。  
  
## <a name="remarks"></a>备注  
 通过此向导生成的注册脚本将注册其 COM 组件，而不是 HKEY_LOCAL_MACHINE HKEY_CURRENT_USER 下的注册表。 若要修改此行为，请设置**为所有用户注册组件**ATL 向导的选项。  
  
## <a name="names"></a>名称  
 指定的对象、 接口和类添加到你的项目的名称。 除**短名称**，可以独立地更改所有其他框。 如果你更改的文本**短名称**，此更改反映在此页中的所有其他框的名称。 如果你更改**组件类**名称中 COM 部分中，更改将反映在**类型**框中，但**接口**名称和**ProgID**执行不是更改。 此命名行为旨在使所有名称轻松地识别为您开发您的控件。  
  
> [!NOTE]
>  **组件类**是在仅非属性化的控件上编辑。 如果你的项目特性化，则不能编辑**组件类**。  
  
### <a name="c"></a>C++  
 介绍如何创建要实现对象的 c + + 类。  
  
 **短名称**  
 设置对象的缩写的名称。 你提供的名称确定类和**组件类**命名的文件 (。CPP 和。H） 名称，接口名称与**类型**名称，除非您单独更改这些字段。  
  
 **类**  
 设置实现对象的类的名称。 此名称根据你在中提供的名称**短名称**前有一个 c，这是典型的类名前缀。  
  
 **.h 文件**  
 设置新对象的类的头文件的名称。 默认情况下，此名称基于你在中提供的名称**短名称**。 单击省略号按钮，以将文件名称保存到你选择的位置，或者将类声明追加到现有文件。 如果选择现有文件时，向导将不将其保存到所选位置直到你单击**完成**。  
  
 向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类声明是否应追加到文件的内容。 单击**是**要追加文件; 单击**否**返回到向导并指定另一个文件的名称。  
  
 **.cpp 文件**  
 设置新对象的类实现文件的名称。 默认情况下，此名称基于你在中提供的名称**短名称**。 单击省略号按钮以将文件名称保存到你选择的位置。 文件不保存到选定的位置，直到您单击**完成**向导中。  
  
 向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类实现是否应追加到文件的内容。 单击**是**要追加文件; 单击**否**返回到向导并指定另一个文件的名称。  
  
 **特性化**  
 指示对象是否使用属性。 如果将对象添加到特性化 ATL 项目中，此选项被选中并且不能更改。 也就是说，你可以将仅特性化的对象添加到具有属性支持创建的项目。  
  
 你可以仅向使用特性的 ATL 项目中添加的特性化的对象。 如果选择此选项为不具有支持的属性的 ATL 项目时，向导会提示你指定是否想要将属性支持添加到项目。  
  
 默认情况下，设置此选项后添加的任何对象都被指定为特性化 （复选框为选中状态）。 你可以清除此框以添加不使用属性的对象。  
  
 请参阅[应用程序设置，ATL 项目向导](../../atl/reference/application-settings-atl-project-wizard.md)和[特性的基本机制](../../windows/basic-mechanics-of-attributes.md)有关详细信息。  
  
### <a name="com"></a>COM  
 为对象提供的 COM 功能有关的信息。  
  
 **组件类**  
 设置包含的一组对象支持的接口的组件类的名称。  
  
> [!NOTE]
>  如果你创建项目使用属性，或者如果在此向导页中指示该控件使用特性，则无法更改此选项，因为 ATL 不包括**组件类**属性。  
  
 **Interface**  
 设置对象的接口的名称。 默认情况下接口名称前有一个"I"。  
  
 **Type**  
 设置会在注册表中显示的对象说明  
  
 **ProgID**  
 设置容器可以使用而不是对象的 CLSID 的名称。 不自动填充此字段。 如果不手动填充此字段，该控件可能不能与其他工具。 例如，无需生成的 ActiveX 控件`ProgID`中均不提供**插入 ActiveX 控件**对话框。 有关对话框中的详细信息，请参阅[插入 ActiveX 控件对话框中](../../windows/insert-activex-control-dialog-box.md)。  
  
## <a name="see-also"></a>请参阅  
 [ATL 控件](../../atl/reference/adding-an-atl-control.md)   
 [将功能添加到复合控件](../../atl/adding-functionality-to-the-composite-control.md)   
 [ATL COM 对象基础知识](../../atl/fundamentals-of-atl-com-objects.md)


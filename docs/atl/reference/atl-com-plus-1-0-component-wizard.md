---
title: "ATL COM + 1.0 组件向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.mts.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding components
- ATL COM+ 1.0 Component Wizard
ms.assetid: 11670681-8671-4122-96a4-2e52f8dadce0
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 2729975c5e823965f4f5c16d5bfe317ce10a3670
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="atl-com-10-component-wizard"></a>ATL COM+ 1.0 组件向导
使用此向导将对象添加到项目中支持 COM + 1.0 服务，包括事务。  
  
 您可以指定对象是否支持双重接口和自动化。 您还可以指示错误信息接口、 增强型的对象控制、 事务和异步消息队列的支持。  
  
## <a name="remarks"></a>备注  
 开头[!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)]，此向导生成的注册脚本将注册其 COM 组件**HKEY_CURRENT_USER**而不是**HKEY_LOCAL_MACHINE**。 若要修改此行为，设置**为所有用户注册组件**ATL 向导的选项。  
  
## <a name="names"></a>名称  
 指定的对象、 接口和类添加到您的项目的名称。 除**短名称**，所有其他框可以相互独立地进行编辑。 如果您更改的文本**短名称**，更改反映在此页中的所有其他框的名称。 如果您更改**Coclass**名称中 COM 部分中，更改将反映在**类型**和**ProgID**框中，但**接口**名称不会更改。 此命名行为旨在使所有名称易被识别为您开发您的控件。  
  
 **短名称**  
 设置对象的缩写的名称。 提供确定的名称`Class`和`Coclass`名称， **.cpp 文件**和**.h 文件**名称，**接口**名称，**类型**名称，与**ProgID**，除非您单独更改这些字段。  
  
 **.h 文件**  
 设置新对象的类的头文件的名称。 默认情况下，此名称取决于您在中提供的名称**短名称**。 单击省略号按钮以保存到您选择的位置的文件名称或类声明追加到现有文件。 如果您选择现有文件，该向导会将其保存到所选位置直到您单击**完成**在向导中。  
  
 该向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类声明是否应追加到文件的内容。 单击**是**追加该文件; 单击**否**以返回到向导并指定其他文件名。  
  
 **类**  
 设置要创建的类的名称。 此名称取决于您在中提供的名称**短名称**前有一个 c，这是典型的类名前缀。  
  
 **.cpp 文件中**  
 设置新对象的类的实现文件的名称。 默认情况下，此名称取决于您在中提供的名称**短名称**。 单击省略号按钮以将文件名称保存到您选择的位置。 该文件不保存到所选的位置，直到您单击**完成**在向导中。  
  
 该向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类实现是否应追加到文件的内容。 单击**是**追加该文件; 单击**否**以返回到向导并指定其他文件名。  
  
 **特性化**  
 指示对象是否使用属性。 如果将对象添加到属性化的 ATL 项目中，此选项被选中并且不能更改。 也就是说，您可以只能特性化将对象添加到创建具有属性支持的项目。  
  
 如果选择此选项为不具有支持的属性的 ATL 项目时，向导会提示您指定是否要将属性支持添加到项目。  
  
 设置此选项后添加任何对象都被指定为特性化默认 （选中复选框）。 您可以清除此框以添加一个不使用属性的对象。  
  
 请参阅[应用程序设置、 ATL 项目向导](../../atl/reference/application-settings-atl-project-wizard.md)和[属性的基本结构](../../windows/basic-mechanics-of-attributes.md)有关详细信息。  
  
### <a name="com"></a>COM  
 为对象提供的 COM 功能有关的信息。  
  
 **组件类**  
 设置的名称包含的一组对象所支持的接口的组件类。  
  
> [!NOTE]
>  如果您使用创建项目属性，或在此向导页中指示 COM + 1.0 组件使用属性，您不能更改此选项，因为 ATL 不包括`coclass`属性。  
  
 **类型**  
 设置不会在注册表中的对象说明  
  
 **接口**  
 设置为对象创建的接口。 此接口包含自定义方法。  
  
 **ProgID**  
 设置容器可以使用而不是该对象的 CLSID 的名称。  
  
## <a name="see-also"></a>另请参阅  
 [ATL COM + 1.0 组件](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)



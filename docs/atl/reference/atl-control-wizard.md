---
title: "ATL 控件向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.control.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
caps.latest.revision: 17
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
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: 586ac14878ccd6908d025d706b72f3c9856d1b39
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="atl-control-wizard"></a>ATL 控件向导
ATL 项目 （或 ATL 支持的 MFC 项目） 插入 ATL 控件。 此向导可用于插入三种类型的控件之一︰  
  
-   标准控件  
  
-   复合控件  
  
-   DHTML 控件  
  
 此外，您可以指定最小控件中移除从接口[接口](../../atl/reference/interfaces-atl-control-wizard.md)列表，作为控件可以在大多数容器中公开的默认值提供。 您可以设置所需的控件中受支持的接口**接口**向导页。  
  
## <a name="remarks"></a>备注  
 此向导生成的注册脚本将注册在 HKEY_CURRENT_USER 而不是 HKEY_LOCAL_MACHINE 下的其 COM 组件。 若要修改此行为，设置**为所有用户注册组件**ATL 向导的选项。  
  
## <a name="names"></a>名称  
 指定的对象、 接口和类添加到您的项目的名称。 除**短名称**，可以单独更改所有其他框。 如果您更改的文本**短名称**，更改反映在此页中的所有其他框的名称。 如果您更改**Coclass**名称中 COM 部分中，更改将反映在**类型**框中，但**接口**名称和**ProgID**不会更改。 此命名行为旨在使所有名称易被识别为您开发您的控件。  
  
> [!NOTE]
>  **Coclass**是在只有非特性化的控件上编辑。 如果您的项目属性化，则无法编辑**Coclass**。  
  
### <a name="c"></a>C++  
 提供创建要实现对象的 c + + 类的信息。  
  
 **短名称**  
 设置对象的缩写的名称。 您提供的名称确定的类和**Coclass**命名的文件 (。CPP 和。H） 名称，该接口名称，与**类型**名称，除非您单独更改这些字段。  
  
 **类**  
 设置实现对象的类的名称。 此名称取决于您在中提供的名称**短名称**前有一个 c，这是典型的类名前缀。  
  
 **.h 文件**  
 设置新对象的类的头文件的名称。 默认情况下，此名称取决于您在中提供的名称**短名称**。 单击省略号按钮以保存到您选择的位置的文件名称或类声明追加到现有文件。 如果您选择一个现有文件，该向导将不将其保存到所选位置直到您单击**完成**。  
  
 该向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类声明是否应追加到文件的内容。 单击**是**追加该文件; 单击**否**以返回到向导并指定其他文件名。  
  
 **.cpp 文件中**  
 设置新对象的类的实现文件的名称。 默认情况下，此名称取决于您在中提供的名称**短名称**。 单击省略号按钮以将文件名称保存到您选择的位置。 该文件不保存到所选的位置，直到您单击**完成**在向导中。  
  
 该向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类实现是否应追加到文件的内容。 单击**是**追加该文件; 单击**否**以返回到向导并指定其他文件名。  
  
 **特性化**  
 指示对象是否使用属性。 如果将对象添加到属性化的 ATL 项目中，此选项被选中并且不能更改。 也就是说，您可以只能特性化将对象添加到创建具有属性支持的项目。  
  
 可以仅对使用属性的 ATL 项目添加特性化的对象。 如果选择此选项为不具有支持的属性的 ATL 项目时，向导会提示您指定是否要将属性支持添加到项目。  
  
 默认情况下，设置此选项后添加的任何对象都被指定为特性化 （选中复选框）。 您可以清除此框以添加一个不使用属性的对象。  
  
 请参阅[应用程序设置、 ATL 项目向导](../../atl/reference/application-settings-atl-project-wizard.md)和[属性的基本结构](../../windows/basic-mechanics-of-attributes.md)有关详细信息。  
  
### <a name="com"></a>COM  
 为对象提供的 COM 功能有关的信息。  
  
 **组件类**  
 设置的名称包含的一组对象所支持的接口的组件类。  
  
> [!NOTE]
>  如果您使用创建项目属性，或在此向导页中指示该控件使用特性，您不能更改此选项，因为 ATL 不包括**coclass**属性。  
  
 **接口**  
 设置对象的接口名称。 默认情况下为接口名称前有一个"I"。  
  
 **类型**  
 设置不会在注册表中的对象说明  
  
 **ProgID**  
 设置容器可以使用而不是该对象的 CLSID 的名称。 不自动填充此字段。 如果不手动填充此字段，该控件可能不能与其他工具。 例如，无需生成的 ActiveX 控件`ProgID`中均不提供**插入 ActiveX 控件**对话框。 有关对话框中的详细信息，请参阅[插入 ActiveX 控件对话框中](../../windows/insert-activex-control-dialog-box.md)。  
  
## <a name="see-also"></a>另请参阅  
 [ATL 控件](../../atl/reference/adding-an-atl-control.md)   
 [将功能添加到复合控件](../../atl/adding-functionality-to-the-composite-control.md)   
 [ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)



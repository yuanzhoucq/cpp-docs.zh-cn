---
title: "ATL 属性页向导 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.ppg.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 项目, 添加属性页"
  - "ATL 属性页向导"
ms.assetid: 6113e325-facd-4f68-b491-144d75209922
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# ATL 属性页向导
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此向导[将属性页添加到 ATL 项目中](../../atl/reference/adding-an-atl-property-page.md)或者具有 ATL 支持的 MFC 项目中。  ATL 属性页提供设置一个或多个 COM 对象的属性（或调用方法）的用户界面。  
  
## 备注  
 从 [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)] 开始，此向导生成的注册脚本将在 **HKEY\_CURRENT\_USER**（而不是 **HKEY\_LOCAL\_MACHINE**）下注册其 COM 组件。  若要修改此行为，请设置 ATL 向导的**“为所有用户注册组件”**选项。  
  
## 名称  
 指定要添加到项目中的对象、接口和类的名称。  除**“简称”**字段外，所有其他框都可以单独编辑。  如果更改“简称”的文本，更改会反映在此页的所有其他框的名称中。  如果更改 COM 区域中的 **Coclass** 的名称，则更改反映在**“类型”**和**“ProgID”**框中。  此命名行为旨在使所有名称在开发属性页时易于识别。  
  
> [!NOTE]
>  **Coclass** 仅对非特性化项目可编辑。  如果项目已特性化，则无法编辑 **Coclass**。  
  
### C\+\+  
 为创建的 C\+\+ 类提供信息以实现对象。  
  
|||  
|-|-|  
|术语|定义|  
|**简称**|设置对象的缩写名称。  您提供的名称确定类和 **CoClass** 名称、文件（**.cpp** 和 **.h**）名称、**“类型”**名称以及 ProgID，除非单独更改这些字段。|  
|**.h 文件**|为新对象的类设置头文件的名称。  默认情况下，此名称基于在“简称”中提供的名称。  单击省略号按钮将该文件名保存到所选位置，或将类声明追加到现有文件。  如果选择现有文件，则直到在向导中单击**“完成”**时，向导才将其保存到所选位置。<br /><br /> 向导不覆盖文件。  如果选择现有文件的名称，则单击“完成”时，向导会提示您指出是否应向该文件的内容中追加类声明。  单击**“是”**追加该文件；单击**“否”**返回到向导并指定另一个文件名。|  
|**类**|设置实现对象的类的名称。  此名称基于在**“简称”**中提供的名称，名称前有一个“C”，这是典型的类名前缀。|  
|**.cpp 文件**|为新对象的类设置实现文件的名称。  默认情况下，此名称基于在“简称”中提供的名称。  单击省略号按钮将文件名保存到所选位置。  直到在向导中单击**“完成”**时，该文件才保存到所选位置。<br /><br /> 向导不覆盖文件。  如果选择现有文件的名称，则单击**“完成”**时，向导会提示您指出是否应向该文件的内容中追加类实现。  单击**“是”**追加该文件；单击**“否”**返回到向导并指定另一个文件名。|  
|**特性化**|指示对象是否使用特性。  如果向特性化 ATL 项目中添加对象，则此选项被选定并且不能更改，也就是说只能将特性化对象添加到创建的具有特性支持的项目中。<br /><br /> 只可向使用特性的 ATL 项目添加特性化对象。  如果为不具有特性支持的 ATL 项目选择此选项，则向导将提示您指定是否为项目添加特性支持。<br /><br /> 默认情况下，设置此选项后添加的任何对象都被指定为特性化（选中此复选框）。  可清除此框以添加不使用特性的对象。<br /><br /> 有关更多信息，请参见 [ATL 项目向导的应用程序设置](../../atl/reference/application-settings-atl-project-wizard.md)和[特性的基本机制](../../windows/basic-mechanics-of-attributes.md)。|  
  
### COM  
 提供有关该对象的 COM 功能的信息。  
  
 **Coclass**  
 设置组件类的名称，该组件类包含对象支持的接口列表。  
  
> [!NOTE]
>  如果使用特性创建项目，或者在此向导页中指示属性页使用特性，则不能更改此选项，因为 ATL 不包括 `coclass` 特性。  
  
 **Type**  
 设置将显示在注册表中的对象说明。  
  
 **ProgID**  
 设置容器可用来代替对象的 CLSID 的名称。  
  
## 请参阅  
 [选项，ATL 属性页向导](../../atl/reference/options-atl-property-page-wizard.md)   
 [字符串，ATL 属性页向导](../../atl/reference/strings-atl-property-page-wizard.md)   
 [Example: Implementing a Property Page](../../atl/example-implementing-a-property-page.md)
---
title: "ATL Active Server Page 组件向导 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.asp.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ASP 组件, 在 ATL 中创建"
  - "ATL Active Server Page 组件向导"
ms.assetid: 5a5cb904-dbbf-44ea-ad3d-2ddd14c1d3c5
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL Active Server Page 组件向导
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此向导将 Active Server Page \(ASP\) 组件插入到项目中。  Microsoft Internet 信息服务 \(IIS\) 将 ASP 组件用作其增强型网页开发结构的一部分。  
  
 通过使用此向导，您可以指定组件的线程模型及其聚合支持。  也可以指示错误信息接口支持、连接点和自由线程封送处理。  
  
## 备注  
 从 [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)] 开始，此向导生成的注册脚本将在 **HKEY\_CURRENT\_USER**（而不是 **HKEY\_LOCAL\_MACHINE**）下注册其 COM 组件。  若要修改此行为，请设置 ATL 向导的**“为所有用户注册组件”**选项。  
  
## 名称  
 指定要添加到项目中的对象、接口和类的名称。  除“简称”外，所有其他框都可以独立于其他框进行编辑。  如果更改“简称”的文本，更改会反映在此页的所有其他框的名称中。  
  
 如果更改 COM 部分中的“CoClass”名称，则更改反映在“类型”和“ProgID”框中，但“接口”名称不更改。  此命名行为旨在使所有名称在开发控件时易于识别。  
  
### C\+\+  
 提供为对象创建的 C\+\+ 类的信息。  
  
 **简称**  
 设置对象的根目录名。  您提供的名称确定 `Class` 和 **Coclass** 名称、**.cpp 文件**和 **.h 文件**名称、**接口**名称、**类型**名称以及 **ProgID**，除非单独更改这些字段。  
  
 **.h 文件**  
 为新对象的类设置头文件的名称。  默认情况下，此名称基于在“简称”中提供的名称。  单击省略号按钮将该文件名保存到所选位置，或将类声明追加到现有文件。  如果选择现有文件，则直到在向导中单击**“完成”**时，向导才将其保存到所选位置。  
  
 向导不覆盖文件。  如果选择现有文件的名称，则单击“完成”时，向导会提示您指出是否应向该文件的内容中追加类声明。  单击**“是”**追加该文件；单击**“否”**返回到向导并指定另一个文件名。  
  
 **类**  
 设置要创建的类的名称。  此名称基于在**“简称”**中提供的名称，名称前有一个“C”，这是典型的类名前缀。  
  
 **.cpp 文件**  
 为新对象的类设置实现文件的名称。  默认情况下，此名称基于在“简称”中提供的名称。  单击省略号按钮将文件名保存到所选位置。  直到在向导中单击**“完成”**时，该文件才保存到所选位置。  
  
 向导不覆盖文件。  如果选择现有文件的名称，则单击**“完成”**时，向导会提示您指出是否应向该文件的内容中追加类实现。  单击**“是”**追加该文件；单击**“否”**返回到向导并指定另一个文件名。  
  
 **特性化**  
 指示对象是否使用特性。  如果将某个对象添加到特性化 ATL 项目中，则此选项被选定而且无法更改。  即只能将特性化对象添加到创建的具有特性支持的项目中。  
  
 如果为不具有特性支持的 ATL 项目选择此选项，则向导将提示您指定是否为项目添加特性支持。  
  
 默认情况下，对于非特性化项目，设置此选项后添加的任何对象都指定为特性化（选中该复选框）。  可清除此框以添加不使用特性的对象。  
  
 有关更多信息，请参见 [ATL 项目向导的应用程序设置](../../atl/reference/application-settings-atl-project-wizard.md)和[特性的基本机制](../../windows/basic-mechanics-of-attributes.md)。  
  
### COM  
 提供有关该对象的 COM 功能的信息。  
  
 **Coclass**  
 设置组件类的名称，该组件类包含对象支持的接口列表。  如果项目或者此对象使用特性，则不能更改此选项，因为 ATL 不包括 **coclass** 特性。  
  
 **Type**  
 设置将出现在 coclass 注册表中的对象说明。  
  
 **接口**  
 设置为对象创建的接口。  此接口包含自定义方法。  
  
 **ProgID**  
 设置容器可用来代替对象的 CLSID 的名称。  
  
## 请参阅  
 [ATL Active Server Page Component](../../atl/reference/adding-an-atl-active-server-page-component.md)
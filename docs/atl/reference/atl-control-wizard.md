---
title: "ATL 控件向导 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.control.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 控件向导"
  - "ATL 项目, 添加控件"
  - "控件 [ATL], 添加到项目"
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
caps.latest.revision: 17
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL 控件向导
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 ATL 项目（或者包含 ATL 支持的 MFC 项目）中插入 ATL 控件。  可使用此向导插入三种控件之一：  
  
-   标准控件  
  
-   复合控件  
  
-   DHTML 控件  
  
 另外，可指定最小控件以从[接口](../../atl/reference/interfaces-atl-control-wizard.md)列表中移除接口，这些是控件在大多数容器中公开的默认接口。  可以在向导的**“接口”**页中设置希望控件支持的接口。  
  
## 备注  
 此向导生成的注册脚本将在 HKEY\_CURRENT\_USER 下，而非 HKEY\_LOCAL\_MACHINE 下注册其 COM 组件。  若要修改此行为，请设置 ATL 向导的**“为所有用户注册组件”**选项。  
  
## 名称  
 指定要添加到项目中的对象、接口和类的名称。  除**“简称”**字段外，所有其他框都可以单独更改。  如果更改**“简称”**的文本，该更改会反映在此页的所有其他框的名称中。  如果更改 COM 部分中的**“CoClass”**名称，则更改反映在**“类型”**框中，但**“接口”**名称和**“ProgID”**不会更改。  此命名行为旨在使所有名称在开发控件时易于识别。  
  
> [!NOTE]
>  **Coclass** 仅在非特性化控件上是可编辑的。  如果项目已特性化，则无法编辑 **Coclass**。  
  
### C\+\+  
 为创建的 C\+\+ 类提供信息以实现对象。  
  
 **简称**  
 设置对象的缩写名称。  您提供的名称确定类和**“Coclass”**名称、文件（.CPP 和 .H）名称、接口名称及**“类型”**名称，除非您单独更改这些字段。  
  
 **类**  
 设置实现对象的类的名称。  此名称基于在**“简称”**中提供的名称，名称前有一个“C”，这是典型的类名前缀。  
  
 **.h 文件**  
 为新对象的类设置头文件的名称。  默认情况下，此名称基于在**“简称”**中提供的名称。  单击省略号按钮将该文件名保存到所选位置，或将类声明追加到现有文件。  如果选择现有文件，则直到单击**“完成”**时，向导才将其保存到所选位置。  
  
 向导不覆盖文件。  如果选择现有文件的名称，则单击**“完成”**时，向导会提示您指出是否应向该文件的内容中追加类声明。  单击**“是”**追加该文件；单击**“否”**返回到向导并指定另一个文件名。  
  
 **.cpp 文件**  
 为新对象的类设置实现文件的名称。  默认情况下，此名称基于在**“简称”**中提供的名称。  单击省略号按钮将文件名保存到所选位置。  直到在向导中单击**“完成”**时，该文件才保存到所选位置。  
  
 向导不覆盖文件。  如果选择现有文件的名称，则单击**“完成”**时，向导会提示您指出是否应向该文件的内容中追加类实现。  单击**“是”**追加该文件；单击**“否”**返回到向导并指定另一个文件名。  
  
 **特性化**  
 指示对象是否使用特性。  如果将某个对象添加到特性化 ATL 项目中，则此选项被选定而且无法更改。  即只能将特性化对象添加到创建的具有特性支持的项目中。  
  
 只可向使用特性的 ATL 项目添加特性化对象。  如果为不具有特性支持的 ATL 项目选择此选项，则向导将提示您指定是否为项目添加特性支持。  
  
 默认情况下，设置此选项后添加的任何对象都被指定为特性化（选中此复选框）。  可清除此框以添加不使用特性的对象。  
  
 有关更多信息，请参见 [ATL 项目向导的应用程序设置](../../atl/reference/application-settings-atl-project-wizard.md)和[特性的基本机制](../../windows/basic-mechanics-of-attributes.md)。  
  
### COM  
 提供有关该对象的 COM 功能的信息。  
  
 **Coclass**  
 设置组件类的名称，该组件类包含对象支持的接口列表。  
  
> [!NOTE]
>  如果使用特性创建项目，或者在此向导页中指示控件使用特性，则不能更改此选项，因为 ATL 不包括**“coclass”**特性。  
  
 **接口**  
 为对象设置接口名称。  默认情况下，接口名称前有一个“I”。  
  
 **Type**  
 设置将显示在注册表中的对象说明。  
  
 **ProgID**  
 设置容器可用来代替对象的 CLSID 的名称。  此字段不会自动填充。  如果不手动填充此字段，则该控件可能无法用于其他工具。  例如，不用 `ProgID` 生成的 ActiveX 控件在**“插入 ActiveX 控件”**对话框中不可用。  有关此对话框的更多信息，请参见[“插入 ActiveX 控件”对话框](../../mfc/insert-activex-control-dialog-box.md)。  
  
## 请参阅  
 [ATL Control](../../atl/reference/adding-an-atl-control.md)   
 [Adding Functionality to the Composite Control](../../atl/adding-functionality-to-the-composite-control.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)
---
title: "ATL 对话框向导 | Microsoft Docs"
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
  - "vc.codewiz.class.atl.dlg.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 对话框向导"
  - "ATL 项目, 添加对话框资源"
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL 对话框向导
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此向导在项目中插入从 [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md) 导出的 ATL 对话框对象。  从 `CAxDialogImpl` 导出的对话框可以承载 ActiveX 控件。  
  
 此向导用默认的**“确定”**和“取消”按钮创建对话框资源。  可使用“资源视图”中的[对话框编辑器](../../mfc/dialog-editor.md)编辑对话框资源并添加 ActiveX 控件。  
  
 此向导在头文件中插入处理默认单击事件的[消息映射](../../atl/message-maps-atl.md)和声明。  有关 ATL 对话框的更多信息，请参见[实现对话框](../../atl/implementing-a-dialog-box.md)。  
  
 **简称**  
 设置 ATL 对话框对象的缩写名称。  所提供的名称确定类名和文件名（.cpp 和 .h），除非单独更改这些字段。  
  
 `Class`  
 设置要创建的类的名称。  此名称基于在“简称”中提供的名称，名称前有一个“C”，这是典型的类名前缀。  
  
 **.h 文件**  
 为新对象的类设置头文件的名称。  默认情况下，此名称基于在“简称”中提供的名称。  单击省略号按钮将该文件名保存到所选位置，或将类声明追加到现有文件。  如果选择现有文件，则直到在向导中单击“完成”时，向导才将其保存到所选位置。  
  
 向导不覆盖文件。  如果选择现有文件的名称，则单击“完成”时，向导会提示您指出是否应向该文件的内容中追加类声明。  单击**“是”**追加该文件；单击**“否”**返回到向导并指定另一个文件名。  
  
 **.cpp 文件**  
 为新对象的类设置实现文件的名称。  默认情况下，此名称基于在“简称”中提供的名称。  单击省略号按钮将文件名保存到所选位置。  直到在向导中单击“完成”时，该文件才保存到所选位置。  
  
 向导不覆盖文件。  如果选择现有文件的名称，则单击“完成”时，向导会提示您指出是否应向该文件的内容中追加类实现。  单击**“是”**追加该文件；单击**“否”**返回到向导并指定另一个文件名。  
  
## 请参阅  
 [ATL Dialog Box](../../atl/reference/adding-an-atl-dialog-box.md)
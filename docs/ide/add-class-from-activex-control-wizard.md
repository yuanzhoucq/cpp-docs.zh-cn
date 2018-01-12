---
title: "从 ActiveX 控件向导添加类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.class.axcontrol
dev_langs: C++
helpviewer_keywords:
- ActiveX Control Wizard
- Add Class from ActiveX Control Wizard [C++]
ms.assetid: 668d801c-5fb6-4176-9191-5c38995a4713
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e2b3b1d2b15db47eea8ebc10b2a73cafba5d6952
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="add-class-from-activex-control-wizard"></a>从 ActiveX 控件添加类向导
使用此向导将从可用的 ActiveX 控件中添加的 MFC 类。 该向导创建从所选的 ActiveX 控件添加每个接口的类。  
  
 **添加类**  
 指定从中创建类的类型库的位置。  
  
|选项|描述|  
|------------|-----------------|  
|**Registry**|在系统中注册的类型库。 已注册的类型库中列出**可用 ActiveX 控件**。|  
|**文件**|类型库不一定在系统中注册，但包含在文件中。 必须提供文件的位置中**位置**。|  
  
 **可用的 ActiveX 控件**  
 指定在系统中当前注册的 ActiveX 控件。 此列表以显示在其接口从选择的 ActiveX 控件**接口**列表。 请参阅[MFC ActiveX 控件： 分发 ActiveX 控件](../mfc/mfc-activex-controls-distributing-activex-controls.md)有关注册 ActiveX 控件的详细信息。  
  
 如果你单击**文件**下**从以下来源添加类**，此框不可更改。  
  
 **位置**  
 指定的 ActiveX 控件的位置。 如果你单击**文件**下**从以下来源添加类**，你可以提供包含类型库的文件的位置。 若要浏览到文件的位置，单击省略号按钮。  
  
 如果你单击**注册表**下**从以下来源添加类**，此框不可更改。  
  
 **接口**  
 ActiveX 控件中当前选定中指定的接口**可用 ActiveX 控件**或中指定的文件中的类型库中**位置**。  
  
|传输按钮|描述|  
|---------------------|-----------------|  
|**>**|添加中当前选定的接口**接口**列表。 如果没有选定接口则不可用。|  
|**>>**|中当前选定 ActiveX 控件中添加的所有接口**可用 ActiveX 控件**或中指定的文件中的类型库中**位置**。|  
|**<**|移除在当前选定的类**生成的类**列表。 不可用，如果没有任何类中当前选定**生成的类**列表。|  
|**<\<**|删除中的所有类**生成的类**列表。 不可用如果**生成的类**列表为空。|  
  
 **生成的类**  
 指定要从使用添加的接口生成的类名称 **>** 或 **>>** 按钮。 你可以单击此框以选择类，然后使用向上或向下键滚动浏览列表中，查看在每个类名`Class`框和文件名称中的**.h 文件**单击时，向导将生成的框**完成**。 你可以在此框中选择一次只有一个类。  
  
 你可以通过此列表中选择它并单击删除类 **<** 。 不需要选择中的类**生成的类**复选框，可以删除所有类; 通过单击 **<<** ，都删除中的所有类**生成的类**框。  
  
 `Class`  
 指定在选定的类名称**生成的类**单击时，该向导将添加的框**完成**。 你可以编辑中的名称`Class`框。  
  
 **.h 文件**  
 设置新对象的类的头文件的名称。 默认情况下，此名称基于你在中提供的名称**生成的类**。 单击省略号按钮，以将文件名称保存到你选择的位置，或者将类声明追加到现有文件。 如果你选择现有文件，向导将不将其保存到所选位置直到你单击**完成**向导中。  
  
 向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类声明是否应追加到文件的内容。 单击**是**要追加文件; 单击**否**返回到向导并指定另一个文件的名称。  
  
 **.cpp 文件**  
 设置新对象的类实现文件的名称。 默认情况下，此名称基于你在中提供的名称**生成的类**。 单击省略号按钮以将文件名称保存到你选择的位置。 文件不保存到选定的位置，直到您单击**完成**向导中。  
  
 向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类实现是否应追加到文件的内容。 单击**是**要追加文件; 单击**否**返回到向导并指定另一个文件的名称。  
  
## <a name="see-also"></a>请参阅  
 [从 ActiveX 控件添加类](../ide/adding-a-class-from-an-activex-control-visual-cpp.md)   
 [自动化客户端：使用类型库](../mfc/automation-clients-using-type-libraries.md)
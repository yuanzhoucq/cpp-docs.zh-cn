---
title: "ATL 对话框向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.dlg.overview
dev_langs: C++
helpviewer_keywords:
- ATL projects, adding dialog resources
- ATL Dialog Wizard
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 003cda9f3b0916cb7c86dfce874840268a64dbff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="atl-dialog-wizard"></a>ATL 对话框向导
此向导将插入项目 ATL 对话框框对象，派生自[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)。 对话框中派生自`CAxDialogImpl`可以承载 ActiveX 控件。  
  
 该向导创建对话框资源具有默认**确定**和**取消**按钮。 你可以编辑对话框资源和添加 ActiveX 控件使用[对话框编辑器](../../windows/dialog-editor.md)资源视图中。  
  
 该向导将插入标头文件[消息映射](../../atl/message-maps-atl.md)单击事件和处理默认值的声明。 请参阅[实现对话框](../../atl/implementing-a-dialog-box.md)有关 ATL 对话框的详细信息。  
  
 **短名称**  
 设置 ATL 对话框对象的缩写的名称。 您提供的名称确定类名称和文件 （.cpp 和.h） 名称，除非您单独更改这些字段。  
  
 `Class`  
 设置要创建的类的名称。 此名称根据你在中提供的名称**短名称**前有一个 c，这是典型的类名前缀。  
  
 **.h 文件**  
 设置新对象的类的头文件的名称。 默认情况下，此名称基于你在中提供的名称**短名称**。 单击省略号按钮，以将文件名称保存到你选择的位置，或者将类声明追加到现有文件。 如果你选择现有文件，向导将不将其保存到所选位置直到你单击**完成**向导中。  
  
 向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类声明是否应追加到文件的内容。 单击**是**要追加文件; 单击**否**返回到向导并指定另一个文件的名称。  
  
 **.cpp 文件**  
 设置新对象的类实现文件的名称。 默认情况下，此名称基于你在中提供的名称**短名称**。 单击省略号按钮以将文件名称保存到你选择的位置。 文件不保存到选定的位置，直到您单击**完成**向导中。  
  
 向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类实现是否应追加到文件的内容。 单击**是**要追加文件; 单击**否**返回到向导并指定另一个文件的名称。  
  
## <a name="see-also"></a>另请参阅  
 [ATL 对话框](../../atl/reference/adding-an-atl-dialog-box.md)


---
title: "ATL 对话框向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.dlg.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding dialog resources
- ATL Dialog Wizard
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
caps.latest.revision: 10
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
ms.openlocfilehash: 43540b1b86dbbf1777e7d5a7f6d8dec5dc618334
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="atl-dialog-wizard"></a>ATL 对话框向导
此向导将插入到该项目 ATL 对话框框中对象，派生自[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)。 对话框中派生自`CAxDialogImpl`如何托管 ActiveX 控件。  
  
 该向导创建对话框资源具有默认**确定**和**取消**按钮。 您可以编辑对话框资源和添加 ActiveX 控件使用[对话框编辑器](../../windows/dialog-editor.md)资源视图中。  
  
 该向导将插入标头文件[消息映射](../../atl/message-maps-atl.md)单击事件和处理默认的声明。 请参阅[实现对话框](../../atl/implementing-a-dialog-box.md)有关 ATL 对话框的详细信息。  
  
 **短名称**  
 设置 ATL 对话框对象的缩写的名称。 你提供的名称确定类名称和文件 （.cpp 和.h） 名称，除非您单独更改这些字段。  
  
 `Class`  
 设置要创建的类的名称。 此名称取决于您在中提供的名称**短名称**前有一个 c，这是典型的类名前缀。  
  
 **.h 文件**  
 设置新对象的类的头文件的名称。 默认情况下，此名称取决于您在中提供的名称**短名称**。 单击省略号按钮以保存到您选择的位置的文件名称或类声明追加到现有文件。 如果您选择现有文件，该向导会将其保存到所选位置直到您单击**完成**在向导中。  
  
 该向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类声明是否应追加到文件的内容。 单击**是**追加该文件; 单击**否**以返回到向导并指定其他文件名。  
  
 **.cpp 文件中**  
 设置新对象的类的实现文件的名称。 默认情况下，此名称取决于您在中提供的名称**短名称**。 单击省略号按钮以将文件名称保存到您选择的位置。 该文件不保存到所选的位置，直到您单击**完成**在向导中。  
  
 该向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类实现是否应追加到文件的内容。 单击**是**追加该文件; 单击**否**以返回到向导并指定其他文件名。  
  
## <a name="see-also"></a>另请参阅  
 [ATL 对话框](../../atl/reference/adding-an-atl-dialog-box.md)



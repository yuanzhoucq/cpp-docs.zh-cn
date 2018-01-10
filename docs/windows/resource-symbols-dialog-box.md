---
title: "资源符号对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.resourcesymbols
dev_langs: C++
helpviewer_keywords:
- New Symbol dialog box
- Resource Symbols dialog box
- Change Symbol dialog box
ms.assetid: 9706cde3-1f48-4fcd-bedb-2b03b455e3c1
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e21f60fb2ca90e9e4825e93103fa74be3563780
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="resource-symbols-dialog-box"></a>“资源符号”对话框
**资源符号**对话框中，你可以添加新的资源符号、 更改显示，或跳到源代码中使用符号所在的位置的符号。  
  
 **名称**  
 显示符号的名称。 有关详细信息，请参阅[符号名限制](../windows/symbol-name-restrictions.md)。  
  
 **“值”**  
 显示符号的数值。 有关详细信息，请参阅[符号值限制](../windows/symbol-value-restrictions.md)。  
  
 **在使用中**  
 选中后，指定符号正由一个或多个资源使用。 “使用者”框中列出一个或多个资源。  
  
 **显示只读符号**  
 选定后，显示只读资源。 默认情况下，“资源符号”对话框中仅显示资源脚本文件中可修改的资源，但通过选中此选项，可修改的资源将显示为加粗文本，而只读资源以纯文本形式显示。  
  
 **通过使用**  
 显示使用符号列表中所选符号的一个或多个资源。 要为给定的资源移动到编辑器中，选择中的资源**使用者**框中，单击**查看使用**。 有关详细信息，请参阅[打开给定符号的资源编辑器](../windows/opening-the-resource-editor-for-a-given-symbol.md)。  
  
 **新建**  
 打开“新建符号”对话框，它可用于为新的符号资源标识符定义名称和值（若有必要）。 有关详细信息，请参阅[创建新符号](../windows/creating-new-symbols.md)。  
  
 **更改**  
 打开“更改符号”对话框，它可用于更改符号的名称或值。 如果符号针对的是使用中的控件或资源，则仅可从相应的资源编辑器更改此符号。 有关详细信息，请参阅[更改未分配的符号](../windows/changing-unassigned-symbols.md)。  
  
 **查看使用**  
 打开包含相应资源编辑器中的符号的资源。 有关详细信息，请参阅[打开给定符号的资源编辑器](../windows/opening-the-resource-editor-for-a-given-symbol.md)。  
  

  
## <a name="requirements"></a>惠?  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [查看资源符号](../windows/viewing-resource-symbols.md)
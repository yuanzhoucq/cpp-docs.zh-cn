---
title: 在快捷键对应表中编辑 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], editing
- keyboard shortcuts [C++], editing in an accelerator table
ms.assetid: 545b650b-4f26-4b20-8431-d942548443bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b0844ab8a4233e2204c42a8d165309c89026fb01
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646223"
---
# <a name="editing-in-an-accelerator-table"></a>在快捷键对应表中编辑
### <a name="to-edit-in-an-accelerator-table"></a>在快捷键对应表中编辑  
  
1.  通过双击中对应的图标打开快捷键对应表[资源视图](../windows/resource-view-window.md)。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在该表中选择一个条目并单击以激活就地编辑。  
  
3.  从下拉组合框中进行选择或就地输入以进行更改。  
  
    -   有关[ID](id-property.md)，从选择列表或输入以进行编辑。  
  
    -   有关[修饰符](../windows/accelerator-modifier-property.md)，从列表中选择。  
  
    -   有关[密钥](../windows/accelerator-key-property.md)，从选择列表或输入以进行编辑。  
  
    -   有关[类型](../windows/accelerator-type-property.md)，选择**ASCII**或**VIRTKEY**从列表中。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。  
  
## <a name="requirements"></a>要求  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [编辑快捷键对应表](../windows/editing-accelerator-tables.md)   
 [快捷键编辑器](../windows/accelerator-editor.md)
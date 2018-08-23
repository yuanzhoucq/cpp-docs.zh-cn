---
title: 销毁列表控件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: edb26671ba775cfa7daf98d39c7eccc9fd4111bd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343277"
---
# <a name="destroying-the-list-control"></a>销毁列表控件
如果您嵌入你[CListCtrl](../mfc/reference/clistctrl-class.md)对象的视图或对话框类中，数据成员作为其所有者被销毁时，它被销毁。 如果你使用[CListView](../mfc/reference/clistview-class.md)，框架销毁控件时销毁视图。  
  
 如果您安排将某些列表数据存储在应用程序中而不是列表控件中，则需要安排释放。 有关详细信息，请参阅[回调项和回调掩码](http://msdn.microsoft.com/library/windows/desktop/bb774736)Windows SDK 中。  
  
 此外，您还要负责释放由您创建并与列表控件对象关联的任何图像列表。  
  
## <a name="see-also"></a>请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)


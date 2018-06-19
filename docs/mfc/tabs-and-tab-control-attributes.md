---
title: 选项卡和选项卡控制属性 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [MFC], reference topics
- tab controls [MFC], attributes
- tabs [MFC]
- tabs [MFC], attributes
- CTabCtrl class [MFC], tab control attributes
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f925f8b6a5c522e22890ee2c1082ae8d709d2220
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381188"
---
# <a name="tabs-and-tab-control-attributes"></a>选项卡和选项卡控件特性
有相当大的控制权的外观和行为的构成选项卡控件的选项卡 ([CTabCtrl](../mfc/reference/ctabctrl-class.md))。 每个选项卡可以标签、 图标、 项状态中，以及与之关联的应用程序定义的 32 位值。 对于每个选项卡上，可以显示图标、 标签，或两者。  
  
 此外，每个选项卡项可以有三种可能状态： 按下、 非按下或突出显示。 仅可以通过修改现有选项卡项设置此状态。 若要修改现有选项卡项，检索通过调用[GetItem](../mfc/reference/ctabctrl-class.md#getitem)，修改`TCITEM`结构 (专门**dwState**和**dwStateMask**数据成员)，然后返回已修改`TCITEM`结构通过调用[SetItem](../mfc/reference/ctabctrl-class.md#setitem)。 如果您需要清除中的所有选项卡项的项状态`CTabCtrl`对象，请调用[DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall)。 此函数将所有选项卡项或除当前选定的所有项的状态重置。  
  
 下面的代码清除所有选项卡项的状态，然后修改第三个项的状态：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]  
  
 有关选项卡特性的详细信息，请参阅[选项卡和选项卡特性](http://msdn.microsoft.com/library/windows/desktop/bb760550)Windows SDK 中。 有关向选项卡控件添加选项卡的详细信息，请参阅[添加选项卡添加到选项卡控件](../mfc/adding-tabs-to-a-tab-control.md)本主题中更高版本。  
  
## <a name="see-also"></a>请参阅  
 [使用 CTabCtrl](../mfc/using-ctabctrl.md)   
 [控件](../mfc/controls-mfc.md)


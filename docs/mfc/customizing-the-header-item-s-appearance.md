---
title: 自定义标头项&#39;s 外观 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e09f8bc0b61e22435ee348968f117940b57132e3
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930870"
---
# <a name="customizing-the-header-item39s-appearance"></a>自定义标头项&#39;s 外观
通过设置*dwStyle*参数首次创建标题控件 ([CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create))，你可以定义的外观和行为的标头项或标头控件本身。  
  
 下面是您可以设置的样式的示例及其用途：  
  
-   若要使标头项看起来像按钮，使用**HDS_BUTTONS**样式。  
  
     如果要执行操作（如按特定列为数据排序）来响应对某个标题项的单击，就像在 Microsoft Outlook 中所做的一样，请使用此样式。  
  
-   若要为标题项提供"热跟踪"外观，鼠标光标移过它们时，使用**HDS_HOTTRACK**样式。  
  
     当指针越过其他平面栏中的某个项时，热跟踪将显示 3D 轮廓。  
  
-   若要指示应隐藏标题控件，使用**HDS_HIDDEN**样式。  
  
     **HDS_HIDDEN**样式指示标题控件旨在用作数据容器而不是可视控件。 此样式不会自动隐藏控件，而会影响 `CHeaderCtrl::Layout` 的行为。 返回的值*cy*的成员`WINDOWPOS`结构将为零，该值指示控件不应为对用户可见。  
  
 有关这些属性的详细信息，请参阅[项](http://msdn.microsoft.com/library/windows/desktop/bb775238)Windows SDK 中。 有关将项添加到标题控件的信息，请参阅[将项添加到标头控件](../mfc/adding-items-to-the-header-control.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控件](../mfc/controls-mfc.md)


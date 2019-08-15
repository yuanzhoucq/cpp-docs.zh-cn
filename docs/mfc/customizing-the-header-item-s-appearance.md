---
title: 自定义标题项&#39;的外观
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
ms.openlocfilehash: 6ce676695d717fcc5d418fe4ed5df91b4f9bca95
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508716"
---
# <a name="customizing-the-header-item39s-appearance"></a>自定义标题项&#39;的外观

通过在首次创建标题控件 ([CHeaderCtrl:: create](../mfc/reference/cheaderctrl-class.md#create)) 时设置*dwStyle*参数, 您可以定义标题项的外观和行为, 或标头控件本身的行为。

下面是您可以设置的样式的示例及其用途：

- 若要使标题项的外观类似于按键, 请使用**HDS_BUTTONS**样式。

   如果要执行操作（如按特定列为数据排序）来响应对某个标题项的单击，就像在 Microsoft Outlook 中所做的一样，请使用此样式。

- 若要使标头项在鼠标光标移过它们时具有 "热跟踪" 外观, 请使用**HDS_HOTTRACK**样式。

   当指针越过其他平面栏中的某个项时，热跟踪将显示 3D 轮廓。

- 若要指示应隐藏标题控件, 请使用**HDS_HIDDEN**样式。

   **HDS_HIDDEN**样式指示标题控件旨在用作数据容器, 而不是可视控件。 此样式不会自动隐藏控件，而会影响 `CHeaderCtrl::Layout` 的行为。 在该`WINDOWPOS`结构的*cy*成员中返回的值将为零, 指示控件对用户不可见。

有关这些属性的详细信息, 请参阅 Windows SDK 中的[项目](/windows/win32/Controls/header-controls)。 有关向标题控件添加项的信息, 请参阅向[标题控件添加项](../mfc/adding-items-to-the-header-control.md)。

## <a name="see-also"></a>请参阅

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

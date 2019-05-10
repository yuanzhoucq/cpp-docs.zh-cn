---
title: 自定义标头项&#39;的外观
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
ms.openlocfilehash: 081260bd5c1cf6335d398a4fd773c9590dbc8030
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241572"
---
# <a name="customizing-the-header-item39s-appearance"></a>自定义标头项&#39;的外观

通过设置*dwStyle*首次创建标头控件时的参数 ([CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create))，可以定义外观和行为的标头项或标题控件本身。

下面是您可以设置的样式的示例及其用途：

- 若要使标题项看起来，使用**HDS_BUTTONS**样式。

   如果要执行操作（如按特定列为数据排序）来响应对某个标题项的单击，就像在 Microsoft Outlook 中所做的一样，请使用此样式。

- 若要为标题项提供"热跟踪"外观，鼠标光标移过它们时，使用**HDS_HOTTRACK**样式。

   当指针越过其他平面栏中的某个项时，热跟踪将显示 3D 轮廓。

- 若要指示应隐藏标题控件，请使用**HDS_HIDDEN**样式。

   **HDS_HIDDEN**样式指示标题控件旨在用作数据容器而不是可视控件。 此样式不会自动隐藏控件，而会影响 `CHeaderCtrl::Layout` 的行为。 中返回的值*cy*的成员`WINDOWPOS`结构将为零，该值指示控件不应对用户可见。

有关这些属性的详细信息，请参阅[项](/windows/desktop/Controls/header-controls)Windows SDK 中。 有关将项添加到标题控件的信息，请参阅[将项添加到标头控件](../mfc/adding-items-to-the-header-control.md)。

## <a name="see-also"></a>请参阅

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

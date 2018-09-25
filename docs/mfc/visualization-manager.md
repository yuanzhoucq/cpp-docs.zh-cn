---
title: 可视化管理器 |Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visualization Manager
ms.assetid: c9dd1365-27ac-42e5-8caa-1004525b4129
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fce4b036c6a6ae3692353ae02e7d36eb5ddfd1e1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398477"
---
# <a name="visualization-manager"></a>可视化管理器

视觉管理器是一个对象，用于控制整个应用程序的外观。 它充当一个类可以为应用程序放置所有绘图代码。 MFC 库包含多个视觉管理器。 如果你想要创建你的应用程序的自定义视图，还可以创建自己的可视化管理器。 下图显示相同的应用程序时启用不同的视觉管理器：

![由 CMFCVisualManagerWindows 呈现的 MyApp](../mfc/media/vmwindows.png "vmwindows")使用 CMFCVisualManagerWindows 视觉管理器的 MyApp

![由 CMFCVisualManagerVS2005 呈现的 MyApp](../mfc/media/vmvs2005.png "vmvs2005")使用 CMFCVisualManagerVS2005 视觉管理器的 MyApp

![由 CMFCVisualManagerOfficeXP 呈现的 MyApp](../mfc/media/vmofficexp.png "vmofficexp")使用 CMFCVisualManagerOfficeXP 视觉管理器的 MyApp

![由 CMFCVisualManagerOffice2003 呈现的 MyApp](../mfc/media/vmoffice2003.png "vmoffice2003")使用 CMFCVisualManagerOffice2003 视觉管理器的 MyApp

![由 CMFCVisualManagerOffice2007 呈现的 MyApp](../mfc/media/msoffice2007.png "msoffice2007")使用 CMFCVisualManagerOffice2007 视觉管理器的 MyApp

默认情况下，visual manager 会维护多个 GUI 元素的绘制代码。 若要提供自定义 UI 元素，您需要重写视觉管理器的相关绘图方法。 有关这些方法的列表，请参阅[CMFCVisualManager 类](../mfc/reference/cmfcvisualmanager-class.md)。 可以重写以提供自定义外观的方法是以开头的所有方法`OnDraw`。

你的应用程序只能有一个`CMFCVisualManager`对象。 若要获取你的应用程序的可视化管理器的指针，调用静态函数[CMFCVisualManager::GetInstance](../mfc/reference/cmfcvisualmanager-class.md#getinstance)。 由于所有视觉管理器继承自`CMFCVisualManager`，则`CMFCVisualManager::GetInstance`方法将获得一个指向相应的视觉管理器，即使您创建自定义视觉管理器。

如果你想要创建自定义视觉管理器，必须从已存在的可视管理器对它进行派生。 要派生的默认类是`CMFCVisualManager`。 但是，如果它更好地类似于您可以在你的应用程序可以使用不同的视觉管理器。 例如，如果你想要使用`CMFCVisualManagerOffice2007`视觉管理器，但希望只可以更改分隔符外观，您可能派生自定义从`CMFCVisualManagerOffice2007`。 在此方案中，你应覆盖仅用于绘制分隔符的方法。

有两种可行方法为应用程序使用特定的视觉管理器。 一种方法是调用[CMFCVisualManager::SetDefaultManager](../mfc/reference/cmfcvisualmanager-class.md#setdefaultmanager)方法并传递相应视觉管理器作为参数。 下面的代码示例演示如何使用`CMFCVisualManagerVS2005`视觉管理器使用此方法：

```cpp
CMFCVisualManager::SetDefaultManager (RUNTIME_CLASS (CMFCVisualManagerVS2005));
```

在应用程序中使用视觉管理器的其他方法是手动创建。 应用程序然后将使用此新的视觉管理器的呈现。 但是，因为可能只有一个`CMFCVisualManager`每个应用程序，必须删除当前的视觉管理器，然后创建一个新的对象。 在以下示例中，`CMyVisualManager`是派生自的自定义视觉管理器`CMFCVisualManager`。 以下方法将更改哪些视觉管理器用于显示应用程序，具体取决于索引：

```cpp
void CMyApp::SetSkin (int index)
{
    if (CMFCVisualManager::GetInstance() != NULL)
    {
        delete CMFCVisualManager::GetInstance();
    }

    switch (index)
    {
    case DEFAULT_STYLE:
        // The following statement creates a new CMFCVisualManager
        CMFCVisualManager::GetInstance();
        break;

    case CUSTOM_STYLE:
        new CMyVisualManager;
        break;

    default:
        CMFCVisualManager::GetInstance();
        break;
    }

    CMFCVisualManager::GetInstance()->RedrawAll();
}
```

## <a name="see-also"></a>请参阅

[用户界面元素](../mfc/user-interface-elements-mfc.md)<br/>
[CMFCVisualManager 类](../mfc/reference/cmfcvisualmanager-class.md)

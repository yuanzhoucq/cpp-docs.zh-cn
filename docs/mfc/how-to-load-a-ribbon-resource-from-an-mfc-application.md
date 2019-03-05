---
title: 如何：从 MFC 应用程序中加载功能区资源
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
ms.openlocfilehash: b7691d4168101209b0e2d2500012a2b4a8e47788
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289550"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>如何：从 MFC 应用程序中加载功能区资源

若要在应用程序中使用功能区资源，请修改应用程序以加载功能区资源。

### <a name="to-load-a-ribbon-resource"></a>加载功能区资源

1. 在 `Ribbon Control` 类中声明 `CMainFrame` 对象。

```
    CMFCRibbonBar m_wndRibbonBar;
```

1. 在 `CMainFrame::OnCreate` 中，创建并初始化功能区控件。

```
    if (!m_wndRibbonBar.Create (this))
{
    return -1;
}

    if (!m_wndRibbonBar.LoadFromResource(IDR_RIBBON))
{
    return -1;
}
```

## <a name="see-also"></a>请参阅

[功能区设计器 (MFC)](../mfc/ribbon-designer-mfc.md)

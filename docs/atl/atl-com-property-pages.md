---
title: ATL COM 属性页
ms.date: 11/04/2016
helpviewer_keywords:
- property pages, COM
- ATL COM objects
- COM property pages
- property pages, ATL
- COM objects, ATL
- ATL property pages
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
ms.openlocfilehash: 90dafc411f3262dc458c5158df049740a9d7a683
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266895"
---
# <a name="atl-com-property-pages"></a>ATL COM 属性页

COM 属性页来设置属性提供一个用户界面 （或调用的方法） 的一个或多个 COM 对象。 属性页会提供丰富的用户界面允许控件属性，以便在设计时设置的广泛使用的 ActiveX 控件。

属性页是 COM 对象实现[IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage)或[IPropertyPage2](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage2)接口。 这些接口提供方法，以便页后，可以与相关联`site`（表示页的容器的 COM 对象） 和大量*对象*（COM 对象的方法将调用以响应更改通过属性页的用户）。 属性页容器负责告诉页面时显示或隐藏其用户界面，以及何时将变更应用所做的用户对基础对象的属性页接口上调用方法。

每个属性页，可以完全独立于其属性可以设置的对象生成。 所有这些属性页需要是若要了解特定接口 （或组的接口） 并为该接口上调用方法提供用户界面。

有关详细信息，请参阅[属性表和属性页](/windows/desktop/com/property-sheets-and-property-pages)Windows SDK 中。

## <a name="in-this-section"></a>本节内容

[指定属性页](../atl/specifying-property-pages.md)<br/>
列出了用于指定您的控件的属性页的步骤，并显示一个示例类。

[属性页](../atl/implementing-property-pages.md)<br/>
列出了用于实现属性页，其中包括要重写方法的步骤。 指导你完成基于 ATLPages 示例程序的完整示例。

## <a name="related-sections"></a>相关章节

[ATLPages 示例](../visual-cpp-samples.md)<br/>
ATLPages 示例中，实现属性页使用的示例抽象`IPropertyPageImpl`。

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
提供了关于如何使用 Active Template Library 进行编程的概念性主题的链接。

## <a name="see-also"></a>请参阅

[概念](../atl/active-template-library-atl-concepts.md)

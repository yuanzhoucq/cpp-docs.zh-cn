---
title: "ATL COM 属性页 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- property pages, COM
- ATL COM objects
- COM property pages
- property pages, ATL
- COM objects, ATL
- ATL property pages
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 08b1c31aeaba25f4eadad5225dd2f5607cf7053c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="atl-com-property-pages"></a>ATL COM 属性页
COM 属性页提供用户界面来设置属性 （或调用方法） 的一个或多个 COM 对象。 属性页广泛使用由 ActiveX 控件提供丰富的用户界面，允许在设计时设置的控件属性。  
  
 属性页是 COM 对象实现[IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246)或[IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996)接口。 这些接口提供允许页后，可以与关联的方法`site`（表示页的容器的 COM 对象） 以及大量的*对象*（COM 对象，其方法将调用以响应更改用户所做的属性页）。 属性页容器负责以通知该页以显示或隐藏其用户界面，以及何时应用所做的更改由用户发起时对基础对象的属性页接口上调用方法。  
  
 每个属性页可以独立于可以设置其属性的对象的完全生成。 所有这些属性页需求是以了解特定接口 （或组的接口） 并为该接口上调用方法提供用户界面。  
  
 有关详细信息，请参阅[属性表和属性页](http://msdn.microsoft.com/library/windows/desktop/ms686577)中[!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  
  
## <a name="in-this-section"></a>本节内容  
 [指定属性页](../atl/specifying-property-pages.md)  
 列出用于指定你的控件的属性页的步骤，并显示一个示例类。  
  
 [属性页](../atl/implementing-property-pages.md)  
 列出了实现属性页中，包括要重写方法的步骤。 指导你完成基于 ATLPages 示例程序的完整示例。  
  
## <a name="related-sections"></a>相关章节  
 [ATLPages 示例](../visual-cpp-samples.md)  
 ATLPages 示例中，实现属性页使用示例抽象`IPropertyPageImpl`。  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 提供了关于如何使用 Active Template Library 进行编程的概念性主题的链接。  
  
## <a name="see-also"></a>请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)


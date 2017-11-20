---
title: "属性和属性页类 (ATL) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.atl.properties
dev_langs: C++
helpviewer_keywords:
- property pages, classes
- properties [ATL], classes
- properties [ATL]
ms.assetid: 31616f98-69f8-48b2-8d58-b8e7d1c2b2d8
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5e8885876d36dcc81169be990c7001aa3052253e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="properties-and-property-pages-classes"></a>属性和属性页类
以下类支持属性和属性页：  
  
-   [CComDispatchDriver](../atl/reference/atl-typedefs.md#ccomdispatchdriver)检索或设置对象的属性通过`IDispatch`指针。  
  
-   [CStockPropImpl](../atl/reference/cstockpropimpl-class.md)实现 atl 支持的常用属性  
  
-   [IPerPropertyBrowsingImpl](../atl/reference/iperpropertybrowsingimpl-class.md)访问对象的属性页中的信息。  
  
-   [IPersistPropertyBagImpl](../atl/reference/ipersistpropertybagimpl-class.md)客户端提供的属性包中存储对象的属性。  
  
-   [IPropertyPageImpl](../atl/reference/ipropertypageimpl-class.md)管理属性表中的特定属性页面。  
  
-   [IPropertyPage2Impl](../atl/reference/ipropertypage2impl-class.md)与类似`IPropertyPageImpl`，但还允许客户端在属性页中选择的特定属性。  
  
-   [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md)获取支持由对象的属性页的 Clsid。  
  
## <a name="related-articles"></a>相关文章  
 [ATL 教程](../atl/active-template-library-atl-tutorial.md)  
  
 [ATL COM 属性页](../atl/atl-com-property-pages.md)  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../atl/atl-class-overview.md)   
 [属性映射宏](../atl/reference/property-map-macros.md)


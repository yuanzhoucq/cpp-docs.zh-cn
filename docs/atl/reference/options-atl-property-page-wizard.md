---
title: 选项，ATL 属性页向导
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.ppg.options
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
ms.openlocfilehash: c92c7a3f03c3ddedbea02647e2317d77a7655609
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298979"
---
# <a name="options-atl-property-page-wizard"></a>选项，ATL 属性页向导

在向导的此页用于定义要创建的属性页的线程处理模型和聚合级别。

- **线程处理模型**

   指定的属性页使用的线程处理模型。

   请参阅[指定项目的线程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)有关详细信息。

   |选项|描述|
   |------------|-----------------|
   |**Single**|仅在主 COM 线程中运行的属性页。|
   |**Apartment**|可以在任何单线程单元中创建的属性页。 默认值。|

- **聚合**

   添加了对要创建的属性页的聚合支持。 请参阅[聚合](../../atl/aggregation.md)有关详细信息。

   |选项|描述|
   |------------|-----------------|
   |**是**|创建可聚合的属性页。|
   |**否**|创建不能聚合的属性页。|
   |**仅**|创建仅可以通过聚合实例化的属性页。|

## <a name="see-also"></a>请参阅

[ATL 属性页向导](../../atl/reference/atl-property-page-wizard.md)<br/>
[字符串，ATL 属性页向导](../../atl/reference/strings-atl-property-page-wizard.md)

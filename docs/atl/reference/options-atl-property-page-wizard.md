---
title: 选项，ATL 属性页向导 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.ppg.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8e7edfb2cb4040238985c6cd78e8f1e5756f4d6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="options-atl-property-page-wizard"></a>选项，ATL 属性页向导
向导的此页用于定义所创建的属性页的线程处理模型和聚合级别。  
  
 **线程处理模型**  
 指定的属性页使用的线程处理模型。  
  
 请参阅[指定项目的线程处理模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)有关详细信息。  
  
|选项|描述|  
|------------|-----------------|  
|`Single`|仅在主要的 COM 线程中运行的属性页。|  
|**单元**|可以在任何单线程单元中创建的属性页。 默认值。|  
  
 **聚合**  
 添加了对你创建的属性页的聚合支持。 请参阅[聚合](../../atl/aggregation.md)有关详细信息。  
  
|选项|描述|  
|------------|-----------------|  
|**是**|创建可聚合的属性页。|  
|**否**|创建不能聚合的属性页。|  
|**仅**|创建只能通过聚合实例化的属性页。|  
  
## <a name="see-also"></a>请参阅  
 [ATL 属性页向导](../../atl/reference/atl-property-page-wizard.md)   
 [字符串，ATL 属性页向导](../../atl/reference/strings-atl-property-page-wizard.md)


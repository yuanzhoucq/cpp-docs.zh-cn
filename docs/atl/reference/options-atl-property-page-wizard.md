---
title: 选项，ATL 属性页向导
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.options
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
ms.openlocfilehash: 205f6d3debafe22373355af12ef88c83d6a01911
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707007"
---
# <a name="options-atl-property-page-wizard"></a>选项，ATL 属性页向导


::: moniker range="vs-2019"

ATL 属性页向导不适用于 Visual Studio 2019 及更高版本。

::: moniker-end

::: moniker range="<=vs-2017"

向导的此页可用于定义要创建的属性页的线程模型和聚合级别。

- **线程模型**

   指定属性页使用的线程模型。

   有关详细信息，请参阅[指定项目的线程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)。

   |选项|说明|
   |------------|-----------------|
   |**单精度**|属性页仅在主 COM 线程中运行。|
   |**单元**|可以在任意一个单线程单元中创建属性页。 默认值。|

- **聚合**

   添加对要创建的属性页的聚合支持。 有关详细信息，请参阅[聚合](../../atl/aggregation.md)。

   |选项|说明|
   |------------|-----------------|
   |**是**|创建可聚合的属性页。|
   |**否**|创建不可聚合的属性页。|
   |**仅限**|创建只能通过聚合来实例化的属性页。|

::: moniker-end

## <a name="see-also"></a>请参阅

[ATL 属性页向导](../../atl/reference/atl-property-page-wizard.md)<br/>
[ATL 属性页向导的“字符串”](../../atl/reference/strings-atl-property-page-wizard.md)

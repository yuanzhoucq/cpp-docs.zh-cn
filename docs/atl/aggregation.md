---
title: 聚合
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
ms.openlocfilehash: 2eec7a801f9fe16bc48fc888d10ce413ec7e79db
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265426"
---
# <a name="aggregation"></a>聚合

有些的时候对象的实现者希望充分利用预构建的另一个对象提供的服务。 此外，它想要此第二个对象显示为第一个自然组成部分。 COM 来实现这两个通过包含关系和聚合目标。

聚合意味着包含 （外部） 对象作为其创建过程的一部分创建包含 （内部） 的对象和由外部公开的内部对象的接口。 对象允许本身或不是可聚合。 如果是，它必须遵循某些规则，聚合才能正常工作。

首先，所有`IUnknown`上包含的对象的方法调用必须委托到包含的对象。

## <a name="see-also"></a>请参阅

[COM 简介](../atl/introduction-to-com.md)<br/>
[重用对象](/windows/desktop/com/reusing-objects)

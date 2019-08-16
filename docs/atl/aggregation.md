---
title: 聚合
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
ms.openlocfilehash: 288af427bd6a8d9baf572dfad8e4a25452694ad9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491974"
---
# <a name="aggregation"></a>聚合

有时, 对象的实现器要利用另一个预先生成的对象提供的服务。 此外, 它还会将第二个对象作为第一个对象的一个自然部分显示。 COM 通过包含和聚合来实现这两个目标。

"聚合" 意味着包含 (外部) 对象会创建包含的 (内部) 对象作为其创建进程的一部分, 并由外部公开内部对象的接口。 对象允许自身可聚合。 如果是, 则必须遵循特定的聚合规则才能正常工作。

主要是, `IUnknown`包含对象上的所有方法调用都必须委托给包含对象。

## <a name="see-also"></a>请参阅

[COM 简介](../atl/introduction-to-com.md)<br/>
[重用对象](/windows/win32/com/reusing-objects)

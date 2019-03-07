---
title: ATL 连接点示例
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
ms.openlocfilehash: 3113637a3f777a56bc0b0994203ce709fbc189d5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265062"
---
# <a name="atl-connection-point-example"></a>ATL 连接点示例

此示例显示了支持的对象[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)作为传出接口：

[!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]

指定时`IPropertyNotifySink`为传出接口，您可以使用类[IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)而不是`IConnectionPointImpl`。 例如：

[!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]

## <a name="see-also"></a>请参阅

[连接点](../atl/atl-connection-points.md)

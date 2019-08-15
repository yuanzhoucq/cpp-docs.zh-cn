---
title: ATL 连接点示例
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
ms.openlocfilehash: f33364cee65031c358fb546312f3fe2b7ae854d3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491796"
---
# <a name="atl-connection-point-example"></a>ATL 连接点示例

此示例显示了一个对象, 该对象支持[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)作为输出接口:

[!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]

指定`IPropertyNotifySink`为传出接口时, 可以使用类`IConnectionPointImpl` [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)而不是。 例如：

[!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]

## <a name="see-also"></a>请参阅

[连接点](../atl/atl-connection-points.md)

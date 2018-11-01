---
title: ATL 连接点示例
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
ms.openlocfilehash: 9312db740171672e6b0f231855408e0d0a9e060d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495987"
---
# <a name="atl-connection-point-example"></a>ATL 连接点示例

此示例显示了支持的对象[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)作为传出接口：

[!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]

指定时`IPropertyNotifySink`为传出接口，您可以使用类[IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)而不是`IConnectionPointImpl`。 例如：

[!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]

## <a name="see-also"></a>请参阅

[连接点](../atl/atl-connection-points.md)


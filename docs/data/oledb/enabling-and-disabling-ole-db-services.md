---
title: 启用和禁用 OLE DB 服务
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
ms.openlocfilehash: df17a55950b03d4d63dea2199e3bc19bedb8a7e3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175337"
---
# <a name="enabling-and-disabling-ole-db-services"></a>启用和禁用 OLE DB 服务

OLE DB 服务组件管理器将使用者向提供商联系以确定是否可以使用单独的服务组件来满足请求的使用者的扩展的功能支持的属性指定的属性进行比较。 例如，如果应用程序请求可滚动游标和提供程序仅支持只进游标，服务组件管理器使用客户端游标引擎服务组件提供可滚动的功能。 如果应用程序依赖于默认提供程序的行集上支持的扩展功能和应用程序不会显式设置要请求的功能，功能可能不会显示在客户端返回的行集上的属性游标引擎。 若要进行互操作，应用程序应始终设置属性来显式请求扩展的功能在需要时。

在某些情况下，可能需要禁用单个 OLE DB 服务很好地配合现有应用程序做出有关提供程序的特征。 OLE DB 服务提供的功能来禁用各个服务或基于连接的连接或使用单个提供程序的所有应用程序的所有服务。

## <a name="see-also"></a>请参阅

[OLE DB 资源池和服务](../../data/oledb/ole-db-resource-pooling-and-services.md)
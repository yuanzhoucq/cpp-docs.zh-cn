---
title: 启用和禁用 OLE DB 服务
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
ms.openlocfilehash: 3016126d09b39ec74f4acb758a2176be05052648
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210959"
---
# <a name="enabling-and-disabling-ole-db-services"></a>启用和禁用 OLE DB 服务

OLE DB 服务组件管理器将使用者指定的属性与提供程序支持的属性进行比较，以确定是否可以使用单个服务组件来满足使用者请求的扩展功能。 例如，如果应用程序请求可滚动的游标，并且提供程序仅支持只进游标，则服务组件管理器使用客户端游标引擎服务组件来提供可滚动功能。 如果应用程序依赖于提供程序的行集上默认支持的扩展功能，并且应用程序未显式设置用于请求该功能的属性，则该功能可能不会出现在客户端返回的行集中游标引擎。 为了能够互操作，应用程序应始终将属性设置为在需要时显式请求扩展功能。

在某些情况下，可能有必要禁用单个 OLE DB 服务，以便与对提供程序的特征进行假设的现有应用程序很好地配合工作。 OLE DB 服务提供了一项功能，即在每个连接的基础上或使用单个提供程序的所有应用程序上禁用各个服务或所有服务。

## <a name="see-also"></a>另请参阅

[OLE DB 资源池和服务](../../data/oledb/ole-db-resource-pooling-and-services.md)

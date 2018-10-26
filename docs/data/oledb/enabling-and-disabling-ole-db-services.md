---
title: 启用和禁用 OLE DB 服务 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 72c890b94d84d170bb3ee01bd02d08fc00f9aa04
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068213"
---
# <a name="enabling-and-disabling-ole-db-services"></a>启用和禁用 OLE DB 服务

OLE DB 服务组件管理器将由所支持的提供商联系以确定是否在调用各个服务组件来满足请求的使用者的扩展的功能的使用者指定的属性进行比较。 例如，如果应用程序请求可滚动游标和提供程序仅支持只进游标，服务组件管理器将调用客户端游标引擎服务组件，可提供可滚动的功能。 如果应用程序依赖于默认提供程序的行集上支持的扩展功能和应用程序未显式设置要请求的功能，功能可能不会显示在客户端返回的行集上的属性游标引擎。 若要进行互操作，应用程序应始终设置属性来显式请求扩展的功能在需要时。

在某些情况下，可能需要禁用单个 OLE DB 服务很好地配合现有应用程序做出有关提供程序的特征。 OLE DB 服务提供的功能来禁用各个服务或基于连接的连接或使用单个提供程序的所有应用程序的所有服务。

## <a name="see-also"></a>请参阅

[OLE DB 资源池和服务](../../data/oledb/ole-db-resource-pooling-and-services.md)
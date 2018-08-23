---
title: 启用和禁用服务提供程序 |Microsoft Docs
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
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 36cb39b467cb413cdf74bef52430cf8caf746199
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340685"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>为提供程序启用或禁用服务
可以启用或禁用默认情况下的所有应用程序访问单个提供程序的单个 OLE DB 服务。 这是通过添加提供程序的 CLSID 下 OLEDB_SERVICES 注册表项具有`DWORD`值，该值指定要启用或禁用的服务下, 表中所示。  
  
|启用的默认服务|关键字值|  
|------------------------------|-------------------|  
|所有服务 （默认值）|0xffffffff|  
|除池和登记|0xfffffffe|  
|除客户端游标|0xfffffffb|  
|除池，登记和客户端游标|0xfffffff0|  
|没有服务|0x00000000|  
|聚合函数，所有服务已禁用|\<缺少密钥 >|  
  
## <a name="see-also"></a>请参阅  
 [启用和禁用 OLE DB 服务](../../data/oledb/enabling-and-disabling-ole-db-services.md)
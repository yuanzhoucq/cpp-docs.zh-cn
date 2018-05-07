---
title: 启用和禁用服务提供程序 |Microsoft 文档
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
ms.openlocfilehash: ef36e35234aa4878e30e70748a5b2ba2975c38dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>为提供程序启用或禁用服务
可以启用或禁用默认情况下的所有应用程序访问的单个提供单独的 OLE DB 服务。 这可通过添加**OLEDB_SERVICES**下提供程序的注册表条目的 CLSID，与`DWORD`值，该值指定要启用或禁用的服务下, 表中所示。  
  
|启用默认服务|关键字值|  
|------------------------------|-------------------|  
|所有服务 （默认值）|0xffffffff|  
|除池和登记|0xfffffffe|  
|除客户端游标|0xfffffffb|  
|除池，自动登记和客户端游标|0xfffffff0|  
|没有任何服务|0x00000000|  
|聚合函数，所有服务已禁用|\<缺少密钥 >|  
  
## <a name="see-also"></a>请参阅  
 [启用和禁用 OLE DB 服务](../../data/oledb/enabling-and-disabling-ole-db-services.md)
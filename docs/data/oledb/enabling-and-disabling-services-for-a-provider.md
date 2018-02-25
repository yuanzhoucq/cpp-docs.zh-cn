---
title: "启用和禁用服务提供程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 60e54d9d02cc819c9eaf7674257d846c537da615
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
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
---
title: 为提供程序启用或禁用服务
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
ms.openlocfilehash: 23579b9561356e95d315c0fbe47132208753afa8
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265121"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>为提供程序启用或禁用服务

可以启用或禁用默认情况下的所有应用程序访问单个提供程序的单个 OLE DB 服务。 这是通过使用指定的服务来启用或禁用下, 表中所示的 DWORD 值添加提供程序的 CLSID 下 OLEDB_SERVICES 注册表项。

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
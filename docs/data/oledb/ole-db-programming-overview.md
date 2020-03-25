---
title: OLE DB 编程概述
ms.date: 10/22/2018
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
ms.openlocfilehash: 2b855e0917ba9cdbdaa38a92473d7bddb4279101
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210062"
---
# <a name="ole-db-programming-overview"></a>OLE DB 编程概述

OLE DB 是一种基于 COM 的高性能数据库技术。 它提供了一种独立于存储数据的窗体访问数据的常用方法。 在典型的业务情形中，公司数据库中不存储大量的信息。 此信息可在文件系统（如 FAT 或 NTFS）、索引顺序文件、个人数据库（如访问）、电子表格（如 Excel）、项目规划应用程序（如项目）和电子邮件（如 Outlook）中找到。 OLE DB 使你能够以相同的方式访问任何类型的数据存储，前提是该数据存储具有 OLE DB 提供程序。

OLE DB 允许开发可访问不同数据源的应用程序，无论这些数据源是否为 DBMS。 OLE DB 使用支持给定数据源的适当 DBMS 功能的 COM 接口，可以实现通用访问。 COM 可减少不必要的服务重复，并可最大程度地提高互操作性。

## <a name="benefits-of-com"></a>COM 的优点

COM 就在这里。 OLE DB 是一组 COM 接口。 通过一组统一的接口访问数据，您可以将数据库组织成一个协作组件矩阵。

基于 COM 规范，OLE DB 定义了可扩展的、可维护的、用于确定和封装 DBMS 功能的一致的可重用部分的接口集合。 这些接口定义了 DBMS 组件（例如行容器、查询处理器和事务协调员）的边界，这将实现对各种信息源的统一事务访问。

## <a name="see-also"></a>另请参阅

[OLE DB 编程](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 模板](../../data/oledb/ole-db-templates.md)

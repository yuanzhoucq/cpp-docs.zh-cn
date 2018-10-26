---
title: OLE DB 编程概述 |Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a58e167b87f95ac243222f852b41f2e6f08aec8d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057940"
---
# <a name="ole-db-programming-overview"></a>OLE DB 编程概述

OLE DB 是一种高性能的基于 COM 的数据库技术。 它提供了访问数据独立于在其中存储的表单的常用方法。 在典型的业务的情况下，大量信息不存储在企业数据库。 索引顺序文件、 个人数据库 （如访问）、 （如 Excel) 的电子表格、 项目规划应用程序 （例如项目） 和电子邮件 （如 Outlook)，将在文件系统 （如 FAT 或 NTFS） 中找到此信息。 OLE DB，可访问任何类型的数据存储方式相同，前提是数据存储区具有 OLE DB 访问接口。

OLE DB，可开发的应用程序访问各种数据源，无论他们是 DBMS。 OLE DB 通用访问可能使用建立适当的 DBMS 功能支持为给定的数据源的 COM 接口。 COM 可减少不必要的重复服务，并最大化不仅在数据源，还在其他应用程序之间的互操作性。

## <a name="benefits-of-com"></a>COM 的优点

这是 COM 的作用所在。 OLE DB 是一组 COM 接口。 通过一组统一的接口访问数据，可以将数据库组织到协作组件的矩阵。

基于 COM 规范，OLE DB 定义接口的因素和封装的 DBMS 功能的一致、 可重用部分的可扩展和可维护的集合。 这些接口定义的 DBMS 组件，如行容器中，查询处理器和事务处理协调器，启用对各种信息源的统一事务性访问的边界。

## <a name="see-also"></a>请参阅

[OLE DB 编程](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 模板](../../data/oledb/ole-db-templates.md)
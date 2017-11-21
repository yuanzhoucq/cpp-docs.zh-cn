---
title: "OLE DB 编程概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1f3d97dda514b3cdb0773adb3d7830e611bca3d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ole-db-programming-overview"></a>OLE DB 编程概述
OLE DB 是一种高性能、 基于 COM 的数据库技术。 它提供访问数据而不考虑在其中存储表单的常用方法。 在典型的业务的情况下，有大量的信息存储在企业数据库外部。 索引顺序文件、 个人数据库 （如访问）、 （如 Excel) 的电子表格、 项目规划应用程序 （例如项目），和电子邮件 （如 Outlook)，将文件系统 （如 FAT 或 NTFS） 中找到此信息。 OLE DB，可在同样的方式访问任何类型的数据存储区，只要数据存储区具有的 OLE DB 提供程序。
  
 OLE DB 允许你开发的应用程序访问各种数据源，无论它们 DBMS。 OLE DB 使得通用访问通过使用为给定的数据源支持相应的 DBMS 功能的 COM 接口。 COM 可减少不必要的重复的服务，并最大化不仅在数据源，还在其他应用程序间的互操作性。  
  
## <a name="benefits-of-com"></a>COM 的优点  
 这是 COM 传入的位置。 OLE DB 是一组 COM 接口。 通过一组统一接口访问数据，你可以将数据库整理到协同组件的矩阵。  
  
 基于 COM 规范，OLE DB 定义的分解，并封装的 DBMS 功能的一致、 可重复使用某些部分的接口的可扩展、 可维护的集合。 这些接口定义 DBMS 组件，如行容器、 查询处理器和事务处理协调器，启用的各种信息源的统一事务性访问的边界。  
 
  
## <a name="see-also"></a>另请参阅  
 [OLE DB 编程](../../data/oledb/ole-db-programming.md)   
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 模板](../../data/oledb/ole-db-templates.md)
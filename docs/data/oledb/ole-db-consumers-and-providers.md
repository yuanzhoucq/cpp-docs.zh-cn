---
title: OLE DB 使用者和提供程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, OLE DB data architecture
- OLE DB providers
- OLE DB consumers, OLE DB data architecture
- OLE DB consumers
- OLE DB, data model
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 170f45a3581846dc588abf06aec170d66aa0d545
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111385"
---
# <a name="ole-db-consumers-and-providers"></a>OLE DB 使用者和提供程序
OLE DB 体系结构使用的模型使用者和提供程序。 使用者发出数据请求。 一个提供程序通过将数据放在以表格格式并将其返回给使用者响应这些请求。 必须提供程序中实现任何使用者可以进行的调用。  
  
 定义从技术上讲，使用者是指任何通过 OLE DB 接口访问数据的系统或应用程序代码 （不一定是 OLE DB 组件）。 提供程序中实现接口。 因此，提供程序是实现 OLE DB 接口来封装对数据的访问，并将其公开给其他对象 （即，使用者） 的任何软件组件。  
  
 根据角色，使用者方法对调用 OLE DB 接口;OLE DB 提供程序实现所需的 OLE DB 接口。  
  
 OLE DB 避免条款客户端和服务器，因为这些角色执行不总是有意义，特别是在 n 层的情况。 因为使用者可能是上一层中提供另一个组件的组件，无法调用它的客户端组件会引起混乱。 此外，提供程序有时更像与服务器的数据库驱动程序。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 编程](../../data/oledb/ole-db-programming.md)   
 [OLE DB 编程概述](../../data/oledb/ole-db-programming-overview.md)
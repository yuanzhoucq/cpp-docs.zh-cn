---
title: "启用和禁用 OLE DB 服务 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 服务 [OLE DB], 启用和禁用"
  - "服务提供程序 [OLE DB]"
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 启用和禁用 OLE DB 服务
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 服务组件管理器将使用者指定的属性与提供程序支持的属性进行比较，确定是否可调用个别的服务组件以满足使用者请求的扩展功能。  例如，如果应用程序请求可滚动的游标而提供程序只支持仅向前游标，服务组件管理器将调用客户端游标引擎服务组件提供可滚动的功能。  如果应用程序依赖提供程序的行集合上默认支持的扩展功能，并且应用程序不显式设置请求该功能的属性，则该功能可能不会出现在客户端游标引擎返回的行集合上。  为了可交互操作，应用程序应该总是将属性设置为在所需的地方显式请求扩展功能。  
  
 某些情况下，可能有必要禁用个别的 OLE DB 服务，以便和臆测提供程序特性的现有应用程序一起正常工作。  OLE DB 服务提供禁用个别服务或者所有服务的能力，或是在每个连接的基础上，或是为使用单个提供程序的所有应用程序。  
  
## 请参阅  
 [OLE DB 资源池和服务](../../data/oledb/ole-db-resource-pooling-and-services.md)
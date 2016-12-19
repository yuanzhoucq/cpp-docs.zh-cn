---
title: "创建简单的只读提供程序 | Microsoft Docs"
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
  - "OLE DB 提供程序模板, 创建提供程序"
  - "OLE DB 提供程序, 创建"
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建简单的只读提供程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用“ATL 项目向导”和“ATL OLE DB 提供程序向导”创建了 OLE DB 提供程序后，可以添加希望支持的其他功能。  通过检查将向使用者发送的数据类型和在什么条件下发送，开始设计提供程序。  尤其重要的是确定是否需要支持命令、事务和其他可选对象。  开头设计好将加快实现和测试的速度。  
  
 示例显示在两部分中：  
  
-   第一部分显示如何[创建简单的只读提供程序](../../data/oledb/implementing-the-simple-read-only-provider.md)，该提供程序读取一对字符串。  
  
-   第二部分显示如何通过添加 `IRowsetLocate` 接口[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)。  
  
## 请参阅  
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)
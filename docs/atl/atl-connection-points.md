---
title: "ATL 连接点 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 连接点"
  - "连接点 [C++], 关于连接点"
  - "连接, 连接点"
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# ATL 连接点
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可连接对象是支持输出接口的对象。  输出接口允许对象与客户端进行通信。  对于每个输出接口，可连接对象都释放一个连接点。  每个输出接口是由调用接收器的对象上的客户端实现的。  
  
 ![连接点](../atl/media/vc2zw31.png "vc2ZW31")  
  
 每个连接点都支持 [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318) 接口。  可连接对象通过 [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857) 接口将其连接点释放到客户端。  
  
## 本节内容  
 [ATL 连接点类](../atl/atl-connection-point-classes.md)  
 简要介绍支持连接点的 ATL 类。  
  
 [将连接点添加到对象](../atl/adding-connection-points-to-an-object.md)  
 概述了用于将连接点添加到对象的步骤。  
  
 [ATL 连接点示例](../atl/atl-connection-point-example.md)  
 提供了声明连接点的一个示例。  
  
## 相关章节  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 提供了关于如何使用 Active Template Library 进行编程的概念性主题的链接。  
  
## 请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)
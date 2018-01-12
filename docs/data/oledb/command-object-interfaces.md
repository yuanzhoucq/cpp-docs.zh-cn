---
title: "命令对象接口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3d83f0a14562985386f0f1f75cfcd99518fea6f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="command-object-interfaces"></a>命令对象接口
命令对象使用`IAccessor`接口来指定参数绑定。 使用者调用`IAccessor::CreateAccessor`，将其传递的数组`DBBINDING`结构。 `DBBINDING`包含有关列绑定 （如类型和长度） 的信息。 提供程序接收这些结构，并确定应如何传输数据和是否需要转换。  
  
 `ICommandText`接口提供了一种方法，以指定的文本命令。 `ICommandProperties`接口处理命令的所有属性。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
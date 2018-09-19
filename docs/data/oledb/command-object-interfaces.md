---
title: 命令对象接口 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ea824fda89ccf45c62145a0fe72e55edc614970a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106937"
---
# <a name="command-object-interfaces"></a>命令对象接口

命令对象使用`IAccessor`接口来指定参数绑定。 使用者可调用`IAccessor::CreateAccessor`，将其传递一个数组`DBBINDING`结构。 `DBBINDING` 包含列绑定 （如类型和长度） 的信息。 提供程序接收这些结构，并确定应如何传输数据以及是否需要转换。  
  
`ICommandText`接口提供了一种方法，以指定的文本命令。 `ICommandProperties`接口处理命令的所有属性。  
  
## <a name="see-also"></a>请参阅  

[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
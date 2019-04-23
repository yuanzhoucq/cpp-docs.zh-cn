---
title: 命令对象接口
ms.date: 10/24/2018
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
ms.openlocfilehash: 755c44cf8d0cb5bf5066197bfd0ead3e0f25e1f9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032396"
---
# <a name="command-object-interfaces"></a>命令对象接口

命令对象使用`IAccessor`接口来指定参数绑定。 使用者可调用`IAccessor::CreateAccessor`，将其传递一个数组`DBBINDING`结构。 `DBBINDING` 包含列绑定 （如类型和长度） 的信息。 提供程序接收这些结构，并确定应如何传输数据以及是否需要转换。

`ICommandText`接口提供了一种方法，以指定的文本命令。 `ICommandProperties`接口处理命令的所有属性。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>

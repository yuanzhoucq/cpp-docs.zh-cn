---
title: 创建简单的只读提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 10/26/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c8fd4e5eb25ab1e8e6b20b576a0688da7b5aa2ef
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216391"
---
# <a name="creating-a-simple-read-only-provider"></a>创建简单的只读提供程序

创建使用 OLE DB 访问接口后**ATL 项目向导**并**ATL OLE DB 提供程序向导**，可以添加你想要支持其他功能。 开始设计您的提供程序通过检查什么类型的数据，将发送给使用者和在什么条件下。 特别是，务必确定你是否需要支持的命令、 事务和其他可选对象。 良好的设计会预先将实现和测试的速度。

在两个部分中提供的示例：

- 第一个部分显示了如何[创建简单的只读提供程序](../../data/oledb/implementing-the-simple-read-only-provider.md)读取字符串的对。

- 第二个部分显示如何[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)通过添加`IRowsetLocate`接口。

## <a name="see-also"></a>请参阅

[创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)<br/>

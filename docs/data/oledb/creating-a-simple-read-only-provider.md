---
title: 创建简单的只读提供程序
ms.date: 10/26/2018
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
ms.openlocfilehash: 2ac8e45ca06a5566923141adf5a22dc6710eeeab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432599"
---
# <a name="creating-a-simple-read-only-provider"></a>创建简单的只读提供程序

创建使用 OLE DB 访问接口后**ATL 项目向导**并**ATL OLE DB 提供程序向导**，可以添加你想要支持其他功能。 开始设计您的提供程序通过检查什么类型的数据，将发送给使用者和在什么条件下。 特别是，务必确定你是否需要支持的命令、 事务和其他可选对象。 良好的设计会预先将实现和测试的速度。

在两个部分中提供的示例：

- 第一个部分显示了如何[创建简单的只读提供程序](../../data/oledb/implementing-the-simple-read-only-provider.md)读取字符串的对。

- 第二个部分显示如何[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)通过添加`IRowsetLocate`接口。

## <a name="see-also"></a>请参阅

[创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)<br/>

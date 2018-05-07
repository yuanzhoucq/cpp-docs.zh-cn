---
title: 创建简单的只读提供程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 2662a071f443967b921c4a8db27713bc7c3e8bb4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="creating-a-simple-read-only-provider"></a>创建简单的只读提供程序
如果你已创建使用 ATL 项目向导和 ATL OLE DB 提供程序向导的 OLE DB 提供程序，你可以添加你想要支持其他功能。 开始通过检查什么类型的数据，则将会发送给使用者和在什么条件下设计你的提供商。 尤其是，务必确定你是否需要支持命令、 事务和其他可选对象。 设计良好，预先将加快实现和测试。  
  
 该示例会显示在两个部分：  
  
-   第一个部分演示如何[创建简单的只读提供程序](../../data/oledb/implementing-the-simple-read-only-provider.md)读取一对字符串。  
  
-   第二个部分显示如何[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)通过添加`IRowsetLocate`接口。  
  
## <a name="see-also"></a>请参阅  
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)
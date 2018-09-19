---
title: 创建简单的只读提供程序 |Microsoft Docs
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
ms.openlocfilehash: 9f951fba45b23b7e4dde92fc11f2faabb53bd43d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101561"
---
# <a name="creating-a-simple-read-only-provider"></a>创建简单的只读提供程序

如果已创建的 OLE DB 访问接口使用 ATL 项目向导和 ATL OLE DB 提供程序向导，可以添加你想要支持其他功能。 开始设计您的提供程序通过检查什么类型的数据将发送给使用者和在什么条件下。 特别是，务必确定你是否需要支持的命令、 事务和其他可选对象。 良好的设计会预先将实现和测试的速度。  
  
在两个部分中提供的示例：  
  
- 第一个部分显示了如何[创建简单的只读提供程序](../../data/oledb/implementing-the-simple-read-only-provider.md)读取字符串的对。  
  
- 第二个部分显示如何[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)通过添加`IRowsetLocate`接口。  
  
## <a name="see-also"></a>请参阅  

[创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)
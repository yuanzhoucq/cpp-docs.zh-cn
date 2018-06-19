---
title: 属性映射 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d7664562ff31f1f5871fab4ce74c1652370a540d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103211"
---
# <a name="property-maps"></a>属性映射
除了会话、 行集，和可选的命令对象中，每个提供程序支持一个或多个属性。 OLE DB 提供程序向导创建的标头文件中包含的属性映射中定义这些属性。 每个标头文件包含为对象或该文件中定义的对象定义的 OLE DB 属性组中的属性的映射。 包含数据源对象的标头文件还包含的属性映射[数据源属性](https://msdn.microsoft.com/en-us/library/ms724188\(v=vs.140\).aspx)。 Session.h 包含的属性映射[会话属性](https://msdn.microsoft.com/en-us/library/ms714221.aspx)。 行集和命令对象驻留在单个标头文件中，调用*projectname*RS.h。 这些属性是的成员[行集属性](https://msdn.microsoft.com/en-us/library/ms711252.aspx)组。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
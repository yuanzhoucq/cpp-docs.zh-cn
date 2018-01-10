---
title: "属性映射 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 05bd576e6e55c94306a8dd648c57a4d606bed696
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="property-maps"></a>属性映射
除了会话、 行集，和可选的命令对象中，每个提供程序支持一个或多个属性。 OLE DB 提供程序向导创建的标头文件中包含的属性映射中定义这些属性。 每个标头文件包含为对象或该文件中定义的对象定义的 OLE DB 属性组中的属性的映射。 包含数据源对象的标头文件还包含的属性映射[数据源属性](https://msdn.microsoft.com/en-us/library/ms724188\(v=vs.140\).aspx)。 Session.h 包含的属性映射[会话属性](https://msdn.microsoft.com/en-us/library/ms714221.aspx)。 行集和命令对象驻留在单个标头文件中，调用*projectname*RS.h。 这些属性是的成员[行集属性](https://msdn.microsoft.com/en-us/library/ms711252.aspx)组。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
---
title: 属性映射 |Microsoft Docs
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
ms.openlocfilehash: 8672cca382d89eda93e624f566f754bd2eb14d0a
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083406"
---
# <a name="property-maps"></a>属性映射

除了会话、 行集以及可选的命令对象，每个提供程序支持一个或多个属性。 由 OLE DB 提供程序向导创建的标头文件中包含的属性映射中定义了这些属性。 每个标头文件包含为该文件中定义的对象定义的 OLE DB 属性组中的属性映射。 包含数据源对象的标头文件还包含的属性映射[数据源属性](https://msdn.microsoft.com/library/ms724188)。 Session.h 包含的属性映射[会话属性](/previous-versions/windows/desktop/ms714221)。 行集和命令对象驻留在单个标头文件中，调用*projectname*RS.h。 这些属性属于[行集属性](/previous-versions/windows/desktop/ms711252)组。  
  
## <a name="see-also"></a>请参阅  

[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
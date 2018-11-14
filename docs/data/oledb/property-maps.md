---
title: 属性映射
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
ms.openlocfilehash: 2d01c2f0d7fb581f9f7e93c1ec100e465a6d92f3
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556452"
---
# <a name="property-maps"></a>属性映射

使用会话、 行集和可选的命令对象，每个提供程序支持一个或多个属性。 这些属性定义中创建的标头文件中存储的属性映射**OLE DB 提供程序向导**。 每个标头文件包含为该文件中定义的对象定义的 OLE DB 属性组中的属性映射。 包含数据源对象的标头文件还包含的属性映射[数据源属性](https://msdn.microsoft.com/library/ms724188)。 `Session.h` 包含的属性映射[会话属性](https://docs.microsoft.com/previous-versions/windows/desktop/ms714221(v=vs.85))。 行集和命令对象是在单个标头文件中，调用*projectname*RS.h。 这些属性属于[行集属性](https://docs.microsoft.com/previous-versions/windows/desktop/ms711252(v=vs.85))组。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>

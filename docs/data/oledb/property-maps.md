---
title: 属性映射
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
ms.openlocfilehash: 174108cac9982e46a62a90f8cb60662527812e47
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575495"
---
# <a name="property-maps"></a>属性映射

使用会话、 行集和可选的命令对象，每个提供程序支持一个或多个属性。 这些属性定义中创建的标头文件中存储的属性映射**OLE DB 提供程序向导**。 每个标头文件包含为该文件中定义的对象定义的 OLE DB 属性组中的属性映射。 包含数据源对象的标头文件还包含的属性映射[数据源属性](https://msdn.microsoft.com/library/ms724188)。 `Session.h` 包含的属性映射[会话属性](/previous-versions/windows/desktop/ms714221)。 行集和命令对象是在单个标头文件中，调用*projectname*RS.h。 这些属性属于[行集属性](/previous-versions/windows/desktop/ms711252)组。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>

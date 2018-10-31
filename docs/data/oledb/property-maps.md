---
title: 属性映射 |Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
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
ms.openlocfilehash: 2c6c3ddc4b19cd9b65203d8a5e675b9ed75720a1
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216456"
---
# <a name="property-maps"></a>属性映射

使用会话、 行集和可选的命令对象，每个提供程序支持一个或多个属性。 这些属性定义中创建的标头文件中存储的属性映射**OLE DB 提供程序向导**。 每个标头文件包含为该文件中定义的对象定义的 OLE DB 属性组中的属性映射。 包含数据源对象的标头文件还包含的属性映射[数据源属性](https://msdn.microsoft.com/library/ms724188)。 `Session.h` 包含的属性映射[会话属性](/previous-versions/windows/desktop/ms714221)。 行集和命令对象是在单个标头文件中，调用*projectname*RS.h。 这些属性属于[行集属性](/previous-versions/windows/desktop/ms711252)组。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>

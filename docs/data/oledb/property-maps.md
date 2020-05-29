---
title: 属性映射
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
ms.openlocfilehash: 79a65290c24ab016d9f81b54b9b7720d5c4ff352
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544554"
---
# <a name="property-maps"></a>属性映射

对于 session、rowset 和 optional 命令对象，每个提供程序都支持一个或多个属性。 这些属性是在存储在由**OLE DB 提供程序向导**创建的标头文件中的属性映射中定义的。 每个标头文件都包含为该文件中定义的对象或对象定义的 OLE DB 属性组中的属性的映射。 包含数据源对象的标头文件还包含数据源[属性](/previous-versions/windows/desktop/ms724188(v=vs.85))的属性映射。 `Session.h` 包含[会话属性](/previous-versions/windows/desktop/ms714221(v=vs.85))的属性映射。 行集和命令对象位于一个名为 "*项目名称*RS .h" 的头文件中。 这些属性是[行集属性](/previous-versions/windows/desktop/ms711252(v=vs.85))组的成员。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>

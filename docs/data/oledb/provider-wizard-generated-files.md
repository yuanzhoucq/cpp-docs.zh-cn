---
title: 提供程序向导生成的文件
ms.date: 10/18/2018
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
ms.openlocfilehash: a9a706463326249135a55bc907cb8a664a3ca808
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037086"
---
# <a name="provider-wizard-generated-files"></a>提供程序向导生成的文件

**ATL OLE DB 提供程序向导**生成以下文件。 下面的主题使用短名称*自定义*，但确切的文件名取决于创建提供程序时所做的选择。

|文件名|描述|
|---------------|-----------------|
|*Custom*RS.cpp|包含命令帮助程序`Execute`方法和提供程序列映射。|
|*自定义*DS.h|实现数据源对象。 此标头文件包含数据源属性的属性映射。|
|*Custom*RS.h|实现的命令和行集对象。 此标头文件包含行集和命令属性的属性映射。|
|*自定义*Sess.h|实现会话对象。 此标头文件包含的会话属性的属性映射。|
|*自定义*.rgs|包含已注册的对象生成**OLE DB 提供程序向导**。|

## <a name="see-also"></a>请参阅

[创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)<br/>

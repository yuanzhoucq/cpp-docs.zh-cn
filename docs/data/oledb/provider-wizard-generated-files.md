---
title: 提供程序向导生成的文件 |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9bc7c85dccdfe095412450d5020fc8a6b42d516
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076966"
---
# <a name="provider-wizard-generated-files"></a>提供程序向导生成的文件

在 ATL OLE DB 提供程序向导将生成以下文件。 下面的主题使用短名称*自定义*，但确切的文件名取决于创建提供程序时所做的选择。

|文件名|描述|
|---------------|-----------------|
|*自定义*RS.cpp|包含命令帮助程序`Execute`方法和提供程序列映射。|
|*自定义*DS.h|实现数据源对象。 此标头文件包含数据源属性的属性映射。|
|*自定义*RS.h|实现的命令和行集对象。 此标头文件包含行集和命令属性的属性映射。|
|*自定义*Sess.h|实现会话对象。 此标头文件包含的会话属性的属性映射。|
|*自定义*.rgs|包含通过 OLE DB 提供程序向导生成的已注册的对象。|

## <a name="see-also"></a>请参阅

[创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)
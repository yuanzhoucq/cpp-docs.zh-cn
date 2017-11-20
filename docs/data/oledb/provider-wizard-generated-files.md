---
title: "提供程序向导生成的文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 24da0ab4b3ab27cdb9a70c0f9cc05e3ca86e117d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="provider-wizard-generated-files"></a>提供程序向导生成的文件
ATL OLE DB 提供程序向导生成以下文件。 下面的主题使用的短名称"MyProvider"，但确切的文件名依赖于时创建提供程序所做的选择。  
  
|文件名|描述|  
|---------------|-----------------|  
|MyProviderRS.cpp|包含命令帮助器`Execute`方法和提供程序列映射。|  
|MyProviderDS.h|实现数据源对象。 此标头文件包含数据源属性的属性映射。|  
|MyProviderRS.h|实现的命令和行集对象。 此标头文件包含行集和命令的属性的属性映射。|  
|MyProviderSess.h|实现的会话对象。 此标头文件包含会话属性的属性映射。|  
|MyProvider.rgs|包含通过 OLE DB 提供程序向导生成的已注册的对象。|  
  
## <a name="see-also"></a>另请参阅  
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)
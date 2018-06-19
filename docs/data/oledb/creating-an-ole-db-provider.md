---
title: 创建 OLE DB 提供程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f649b5b4c79c4148d0aed026b044485ca2b1eaa7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097102"
---
# <a name="creating-an-ole-db-provider"></a>创建 OLE DB 提供程序
创建 OLE DB 提供程序的建议的方法是使用向导来创建 ATL COM 项目和提供程序，然后修改使用 OLE DB 模板的文件。 在自定义你的提供商，你可以注释掉不需要的属性，然后添加可选接口。  
  
 基本步骤如下：  
  
1.  使用 ATL 项目向导来创建基本项目文件和 ATL OLE DB 提供程序向导创建提供程序 (选择**ATL OLE DB 访问接口**中的 Visual c + + 文件夹从**添加类**)。  
  
2.  修改中的代码`Execute`CMyProviderRS.h 中的方法。 有关示例，请参阅[字符串读入 OLE DB 提供程序](../../data/oledb/reading-strings-into-the-ole-db-provider.md)。  
  
3.  编辑 MyProviderDS.h、 MyProviderSess.h 和 MyProviderRS.h 中的属性映射。 向导将创建包含提供程序可能实现的所有属性的属性映射。 经过属性映射，删除或注释掉你的提供程序不需要支持的属性。  
  
4.  更新 PROVIDER_COLUMN_MAP，可找到 MyProviderRS.h 中。 有关示例，请参阅[存储字符串中的 OLE DB 提供程序](../../data/oledb/storing-strings-in-the-ole-db-provider.md)。  
  
5.  当你准备好测试你的提供程序，可以通过尝试查找提供程序枚举中的提供程序对其进行测试。 枚举中找到提供程序的测试代码的示例，请参阅[CATDB](http://msdn.microsoft.com/en-us/003d516b-2bf6-444e-8be5-4ebaa0b66046)和[DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832)示例或中的示例[实现简单使用的者](../../data/oledb/implementing-a-simple-consumer.md)。  
  
6.  添加所需的任何其他接口。 有关示例，请参阅[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)。  
  
    > [!NOTE]
    >  默认情况下，向导生成代码都符合 OLE DB 级别 0。 若要确保你的应用程序保持符合级别 0，请不任何向导生成接口从代码中删除。  
  
## <a name="see-also"></a>请参阅  
 [CATDB](http://msdn.microsoft.com/en-us/003d516b-2bf6-444e-8be5-4ebaa0b66046)   
 [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832)
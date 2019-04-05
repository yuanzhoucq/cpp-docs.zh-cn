---
title: 创建 OLE DB 提供程序
ms.date: 10/13/2018
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
ms.openlocfilehash: 3e46e87b0d5d538a0f9fd7e231debfef3fa95210
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59036109"
---
# <a name="creating-an-ole-db-provider"></a>创建 OLE DB 提供程序

创建 OLE DB 提供程序的建议的方法是使用这些向导创建的 ATL COM 项目和提供程序，然后修改使用 OLE DB 模板的文件。 自定义您的提供程序，你可以注释掉不需要的属性并添加可选接口。

基本步骤如下：

1. 使用**ATL 项目向导**若要创建基本项目文件并**ATL OLEDB 提供程序向导**来创建提供程序 (选择**ATL OLEDB 提供程序**从**已安装** > **Visual c + +** > **ATL**文件夹中的**添加新项**)。

   > [!NOTE]
   > 该项目必须包括 MFC 支持，然后再添加**ATL OLEDB 提供程序**。

1. 修改中的代码`Execute`中的方法[CCustomRowset(CustomRS.h)](cmyproviderrowset-myproviderrs-h.md)。 有关示例，请参阅[字符串读入 OLE DB 提供程序](../../data/oledb/reading-strings-into-the-ole-db-provider.md)。

1. 该属性映射中编辑[CustomDS.h](cmyprovidersource-myproviderds-h.md)， [CustomSess.h](cmyprovidersession-myprovidersess-h.md)，并[CustomRS.h](cmyproviderrowset-myproviderrs-h.md)。 向导将创建包含一个提供程序可能会实现的所有属性的属性映射。 完成属性映射，并删除或注释掉您的提供程序不需要支持的属性。

1. 更新 PROVIDER_COLUMN_MAP，可以在中找到[CCustomRowset(CustomRS.h)](cmyproviderrowset-myproviderrs-h.md)。 有关示例，请参阅[存储字符串中的 OLE DB 提供程序](../../data/oledb/storing-strings-in-the-ole-db-provider.md)。

1. 当准备好测试你的提供商，可以通过尝试查找提供程序枚举中的提供程序对它进行测试。 枚举中找到提供程序的测试代码的示例，请参阅[CATDB](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb)并[DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer)示例或中的示例[实现简单使用的者](../../data/oledb/implementing-a-simple-consumer.md)。

1. 添加所需的任何其他接口。 有关示例，请参阅[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)。

   > [!NOTE]
   > 默认情况下，向导生成是符合 OLE DB 级别 0 的代码。 为确保你的应用程序保持符合级别 0，不要删除任何向导生成的接口从代码。

## <a name="see-also"></a>请参阅

[CatDB 示例：数据源架构浏览器](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb)<br/>
[DBViewer 示例：数据库浏览器](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer)

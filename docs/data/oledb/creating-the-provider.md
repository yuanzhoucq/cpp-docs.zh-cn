---
title: 创建提供程序
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
ms.openlocfilehash: 7a8b4caf85ff7d0310c97cb953739796cca21c43
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707582"
---
# <a name="creating-the-provider"></a>创建提供程序

::: moniker range="vs-2019"

ATL OLE DB 提供程序向导不适用于 Visual Studio 2019 及更高版本。

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>使用 ATL OLE DB 提供程序向导创建 OLE DB 提供程序的具体步骤

1. 右键单击项目。

1. 在快捷菜单中，依次单击“添加”和“添加类”。

1. 在“添加类”对话框中，依次转到“已安装”>“Visual C++”>“ATL”下，选择“ATL OLEDB 提供程序”图标，再单击“打开”。

1. 在 ATL OLE DB 提供程序向导的“短名称”框中，输入提供程序的短名称。 下面的主题使用短名称“Custom”，但你可以使用其他名称。 其他名称框会根据你输入的名称进行填充。

1. 如果需要，编辑其他名称框。 除了对象和文件名外，还可以编辑以下内容：

   - **组件类**：COM 用于创建提供程序的名称。

   - **编程 ID**：编程标识符，可用来代替 GUID 的文本字符串。

   - **版本**：与“编程 ID”和“组件类”一起用来生成版本从属编程 ID。

1. 单击 **“完成”**。

::: moniker-end

## <a name="see-also"></a>请参阅

[创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)

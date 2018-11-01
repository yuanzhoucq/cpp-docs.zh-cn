---
title: 创建提供程序
ms.date: 10/15/2018
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
ms.openlocfilehash: 05ab045e104e3035f8ccd2fa1924b6959164b8d4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538172"
---
# <a name="creating-the-provider"></a>创建提供程序

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>使用 ATL OLE DB 提供程序向导创建 OLE DB 提供程序

1. 右键单击该项目。

1. 在快捷菜单上，单击**外**，然后单击**添加类**。

1. 在中**添加类**对话框中的**已安装** > **Visual c + +** > **ATL**，选择**ATL OLEDB 提供程序**图标，，然后单击**打开**。

1. 在中**ATL OLE DB 提供程序向导**，输入在提供程序的短名称**短名称**框。 下面的主题使用短名称*自定义*，但你可以使用其他名称。 其他名称框填充根据输入的名称。

1. 如果需要，编辑的其他名称框。 除了对象和文件名称，可以编辑以下：

   - **组件类**: COM 使用来创建提供程序的名称。

   - **ProgID**： 是可用来代替 GUID 的文本字符串的编程标识符。

   - **版本**： 具有 ProgID 和组件类用于生成版本依赖型编程 id。

1. 单击 **“完成”**。

## <a name="see-also"></a>请参阅

[创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)

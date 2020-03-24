---
title: 为提供程序创建项目
ms.date: 10/22/2018
helpviewer_keywords:
- ATL projects, creating
- OLE DB providers, projects
- projects [C++], creating
ms.assetid: 076a75de-1d4b-486a-bcf8-9c0f6b049fa2
ms.openlocfilehash: f2ff42ba8a2e908f672db7e96fc9f24f51a1fd9b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211401"
---
# <a name="creating-a-project-for-the-provider"></a>为提供程序创建项目

## <a name="to-create-a-project-in-which-the-ole-db-provider-will-reside"></a>创建一个将驻留 OLE DB 提供程序的项目

1. 在“文件”菜单中，单击“新建”，并单击“项目”。

   将显示“新建项目”对话框。

1. 在 "**项目类型**" 窗格中，单击**安装**的 > **Visual C++**  > **MFC/ATL**文件夹。 在 "**模板**" 窗格中单击 " **ATL 项目**"。

    > [!NOTE]
    > 在 visual Studio 的早期版本中，在 "**已安装**的 > **模板**" 下查找 >  **C++ Visual** > **ATL**的项目类型。

1. 在 "**名称**" 框中，输入项目的名称，然后单击 **"确定"** 。

   此时将显示 " **ATL 项目" 向导**。

1. 在**ATL 项目向导**中，选择 "**应用程序类型**" 的**动态链接库（DLL）** 。

1. 单击“完成”。

## <a name="see-also"></a>另请参阅

[创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)

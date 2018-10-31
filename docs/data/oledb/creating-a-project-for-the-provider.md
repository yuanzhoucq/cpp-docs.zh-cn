---
title: 为提供程序创建项目 |Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, creating
- OLE DB providers, projects
- projects [C++], creating
ms.assetid: 076a75de-1d4b-486a-bcf8-9c0f6b049fa2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0f4049190ac30cfff634d4cfef82410ccfdf1314
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063073"
---
# <a name="creating-a-project-for-the-provider"></a>为提供程序创建项目

## <a name="to-create-a-project-in-which-the-ole-db-provider-will-reside"></a>若要创建的 OLE DB 访问接口将驻留在其中一个项目

1. 在“文件”菜单上，单击“新建”，然后单击“项目”。

   此时将出现 “新建项目” 对话框。

1. 在中**项目类型**窗格中，单击**已安装** > **Visual c + +** > **MFC/ATL**文件夹。 在中**模板**窗格中，单击**ATL 项目**。

    > [!NOTE]
    > 在以前版本的 Visual Studio 中，找到下的项目类型**已安装** > **模板** > **Visual c + +**  > **ATL**。

1. 在中**名称**框中，输入项目的名称，然后单击**确定**。

   **ATL 项目向导**出现。

1. 在中**ATL 项目向导**，选择**动态链接库 (DLL)** 有关**应用程序类型**。

1. 单击 **“完成”**。

## <a name="see-also"></a>请参阅

[创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)
---
title: 将 Visual C++ 应用程序部署到应用本地文件夹
ms.date: 09/17/2018
helpviewer_keywords:
- deploying Visual C++ applications
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
ms.openlocfilehash: 33edf4bb736fad62928e11dd0550af6640d411ac
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746755"
---
# <a name="walkthrough-deploying-a-visual-c-application-to-an-application-local-folder"></a>演练：将 Visual C++ 应用程序部署到应用程序本地文件夹

介绍如何通过将文件复制到其文件夹来部署 Visual C ++ 应用程序。

## <a name="prerequisites"></a>系统必备

- 一台已安装 Visual Studio 的计算机。

- 另一台没有 Visual C++ 库的计算机。

### <a name="to-deploy-an-application-to-an-application-local-folder"></a>将应用程序部署到应用程序本地文件夹

1. 请按照[演练：使用安装项目部署 Visual C++ 应用程序](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)中的步骤创建和生成 MFC 应用程序。

1. 从 \\VC\\redist\\version 文件夹的 Visual Studio 安装目录中复制相应的 MFC 和 C 运行时 (CRT) 库文件，然后将它们粘贴到 MFC 项目的 \Release\ 文件夹中。 有关可能必须复制的其他文件的详细信息，请参阅[确定要重新分发的 DLL](determining-which-dlls-to-redistribute.md)。

1. 在没有 Visual C++ 库的第二台计算机上运行 MFC 应用程序。

   1. 复制 \Release\ 文件夹中的内容，并在第二台计算机上将复制的内容粘贴到应用程序文件夹中。

   1. 在第二台计算机上运行应用程序。

   此应用程序成功运行，因为 Visual C++ 库已位于应用程序本地文件夹。

## <a name="see-also"></a>请参阅

[部署示例](deployment-examples.md)<br/>

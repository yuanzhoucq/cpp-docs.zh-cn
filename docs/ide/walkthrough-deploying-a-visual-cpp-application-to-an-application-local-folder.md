---
title: 将 Visual C++ 应用程序部署到应用本地文件夹 | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying Visual C++ applications
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f749a288ac08adfb5df5291ce3dd92b95c2301e8
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234237"
---
# <a name="walkthrough-deploying-a-visual-c-application-to-an-application-local-folder"></a>演练：将 Visual C++ 应用程序部署到应用程序本地文件夹

介绍如何通过将文件复制到其文件夹来部署 Visual C ++ 应用程序。  
  
## <a name="prerequisites"></a>系统必备  
  
- 一台已安装 Visual Studio 的计算机。  
  
- 另一台没有 Visual C++ 库的计算机。  
  
### <a name="to-deploy-an-application-to-an-application-local-folder"></a>将应用程序部署到应用程序本地文件夹  
  
1. 按照[演练：使用安装项目部署 Visual C++ 应用程序](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)中的步骤创建并生成 MFC 应用程序。  
  
1. 从 \\VC\\redist\\version 文件夹的 Visual Studio 安装目录中复制相应的 MFC 和 C 运行时 (CRT) 库文件，然后将它们粘贴到 MFC 项目的 \Release\ 文件夹中。 有关可能必须复制的其他文件的详细信息，请参阅[确定要重新分发的 DLL](determining-which-dlls-to-redistribute.md)。  
  
1. 在没有 Visual C++ 库的第二台计算机上运行 MFC 应用程序。  
  
   1. 复制 \Release\ 文件夹中的内容，并在第二台计算机上将复制的内容粘贴到应用程序文件夹中。  
  
   1. 在第二台计算机上运行应用程序。  
  
   此应用程序成功运行，因为 Visual C++ 库已位于应用程序本地文件夹。  
  
## <a name="see-also"></a>请参阅  

[部署示例](deployment-examples.md)<br/>

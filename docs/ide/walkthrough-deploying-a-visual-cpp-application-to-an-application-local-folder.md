---
title: "部署到应用程序本地文件夹 Visual c + + 应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: deploying Visual C++ applications
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1d9a92a5fef96932f1d6a58503fe6355b5a410ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-deploying-a-visual-c-application-to-an-application-local-folder"></a>演练：将 Visual C++ 应用程序部署到应用程序本地文件夹
描述如何将 Visual c + + 应用程序部署通过将文件复制到其文件夹。  
  
## <a name="prerequisites"></a>系统必备  
  
-   安装了 Visual Studio 的计算机。  
  
-   没有 Visual c + + 库的另一台计算机。  
  
### <a name="to-deploy-an-application-to-an-application-local-folder"></a>若要应用程序部署到应用程序本地文件夹  
  
1.  创建和生成 MFC 应用程序中的步骤[演练： 部署 Visual c + + 应用程序通过使用安装项目](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)。  
  
2.  复制所需的 MFC 和 C 运行时 (CRT) 库文件-例如，对于 x86 平台和 Unicode 支持、 复制 mfc100u.dll 和从 files\microsoft Visual Studio 10.0\VC\redist\x86\—and msvcr100.dll 然后将它们粘贴的 \Release\ 文件夹中MFC 项目。 有关你可能必须将复制其他文件的详细信息，请参阅[确定要重新分发的 Dll](../ide/determining-which-dlls-to-redistribute.md)。  
  
3.  在没有 Visual c + + 库的第二个计算机上运行 MFC 应用程序。  
  
    1.  \Release\ 文件夹的内容复制并将它们粘贴在第二台计算机上的应用程序文件夹中。  
  
    2.  在第二台计算机上运行应用程序。  
  
     应用程序将成功运行，因为 Visual c + + 库中可用的应用程序本地文件夹。  
  
## <a name="see-also"></a>请参阅  
 [部署示例](../ide/deployment-examples.md)
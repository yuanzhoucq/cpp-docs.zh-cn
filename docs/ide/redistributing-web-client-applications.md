---
title: 重新发布 Web 客户端应用程序 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Web applications [C++], redistributing
- deploying applications [C++], Web applications
- Internet applications [C++], redistributing
- application deployment [C++], Web applications
ms.assetid: fe05988b-dee8-4a46-b381-016b5103a6bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92bd843b24ee13b3d606ba8bb4f4f1cc265e8e5d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323191"
---
# <a name="redistributing-web-client-applications"></a>重新发布 Web 客户端应用程序
如果应用程序使用实现 WebBrowser 控件的 MFC 类（例如，`CHtmlView` 或 `CHtmlEditView`，则必须至少在目标计算机上精简地安装 Microsoft Internet Explorer 4.0 或更高版本。  
  
 安装最新版本的 Internet Explorer 还可确保目标计算机具有最新的通用控件文件。  
  
 以下知识库文章中提供了有关安装最少 Internet Explorer 组件的信息：  
  
-   Q185375 - 如何：创建 Internet Explorer 的单一 EXE 安装 ([http://support.microsoft.com/support/kb/articles/q185/3/75.asp](http://support.microsoft.com/support/kb/articles/q185/3/75.asp))  
  
 可以在 MSDN Library 或 [http://support.microsoft.com](http://support.microsoft.com) 查找知识库文章。  
  
## <a name="see-also"></a>请参阅  
 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)
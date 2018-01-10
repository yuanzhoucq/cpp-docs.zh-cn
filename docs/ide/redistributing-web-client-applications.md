---
title: "重新分发 Web 客户端应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Web applications [C++], redistributing
- deploying applications [C++], Web applications
- Internet applications [C++], redistributing
- application deployment [C++], Web applications
ms.assetid: fe05988b-dee8-4a46-b381-016b5103a6bf
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e764e42cb558d2e13e0609cb139e9538a72d09ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="redistributing-web-client-applications"></a>重新发布 Web 客户端应用程序
如果你的应用程序将使用实现 WebBrowser 控件的 MFC 类 (例如，`CHtmlView`或`CHtmlEditView`)，Microsoft Internet Explorer 4.0 或更高版本必须至少按最小方式安装在目标计算机上。  
  
 安装最新版本的 Internet Explorer 还可确保目标计算机具有的最新的公共控件文件。  
  
 有关安装最小的 Internet 资源管理器组件的信息可用于以下知识库文章：  
  
-   Q185375，如何： 创建 Internet Explorer 的单个 EXE 安装 ([http://support.microsoft.com/support/kb/articles/q185/3/75.asp](http://support.microsoft.com/support/kb/articles/q185/3/75.asp))  
  
 你可以在 MSDN 库中或在查找知识库文章[http://support.microsoft.com](http://support.microsoft.com)。  
  
## <a name="see-also"></a>请参阅  
 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)
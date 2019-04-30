---
title: 重新发布 Web 客户端应用程序
ms.date: 11/04/2016
helpviewer_keywords:
- Web applications [C++], redistributing
- deploying applications [C++], Web applications
- Internet applications [C++], redistributing
- application deployment [C++], Web applications
ms.assetid: fe05988b-dee8-4a46-b381-016b5103a6bf
ms.openlocfilehash: f821541efd8705e61b3292cc63713d280fd17a68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388119"
---
# <a name="redistributing-web-client-applications"></a>重新发布 Web 客户端应用程序

如果应用程序使用实现 WebBrowser 控件的 MFC 类（例如，`CHtmlView` 或 `CHtmlEditView`，则必须至少在目标计算机上精简地安装 Microsoft Internet Explorer 4.0 或更高版本。

安装最新版本的 Internet Explorer 还可确保目标计算机具有最新的通用控件文件。 有关详细信息，请参阅[安装和配置 Internet Explorer 11](/internet-explorer/ie11-deploy-guide/install-and-deploy-ie11)

## <a name="see-also"></a>请参阅

[部署桌面应用程序](deploying-native-desktop-applications-visual-cpp.md)

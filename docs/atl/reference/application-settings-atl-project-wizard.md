---
title: 应用程序设置，ATL 项目向导
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.atl.com.appset
helpviewer_keywords:
- ATL Project Wizard, application settings
ms.assetid: d48c9fc5-f439-49fd-884c-8bcfa7d52991
ms.openlocfilehash: bd9d5c6ef1ccb86f2968b1e2d2706092b6db45e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62248995"
---
# <a name="application-settings-atl-project-wizard"></a>应用程序设置，ATL 项目向导

使用**应用程序设置**ATL 项目向导来设计和将基本功能添加到新的 ATL 项目页。

## <a name="server-type"></a>服务器类型

选择三种服务器类型之一：

- **动态链接库 (DLL)**

   选择要创建一个进程内服务器。

- **可执行文件 (EXE)**

   选择此选项可以创建本地进程外服务器。 此选项不允许对 MFC 或 COM + 1.0 的支持。 它不允许为合并代理/存根 （stub） 代码。

- **Service (EXE)**

   选择此项可创建 Windows 启动时在后台运行的 Windows 应用程序。 此选项不允许对 MFC 或 COM + 1.0 的支持或不允许合并代理/存根 （stub） 代码。

## <a name="additional-options"></a>附加选项

> [!NOTE]
> 所有其他选项都适用于仅限 DLL 项目。

- **允许合并代理/存根 （stub） 代码**

   选择**允许合并代理/存根代码**为方便起见需要封送接口时的复选框。 此选项将在相同的 MIDL 生成的代理和存根 （stub） 代码可执行文件作为服务器。

- **MFC 支持**

   选择此选项可以指定您的对象包括 MFC 支持。 此选项将项目链接到 MFC 库，以便可以访问的任何类和它们所包含的函数。

- **支持 COM + 1.0**

   选择要修改的项目生成设置来支持 COM + 1.0 组件。 除了标准库的列表，该向导将添加 COM + 1.0 组件特定的库 comsvcs.lib

   此外，mtxex.dll 是你的应用程序启动时加载在主机系统上的延迟。

- **支持组件注册机构**

   如果在 ATL 项目包含对 COM + 1.0 组件的支持，可以设置此选项。 组件注册器使您的 COM + 1.0 对象获取一系列组件、 注册组件，或取消组件注册 （单独或全部同时）。

## <a name="see-also"></a>请参阅

[ATL 项目向导](../../atl/reference/atl-project-wizard.md)<br/>
[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)<br/>
[默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)

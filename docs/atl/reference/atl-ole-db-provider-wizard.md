---
title: ATL OLE DB 提供程序向导 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.provider.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL OLE DB Provider Wizard
- ATL projects, adding ATL OLE DB providers
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6857bf80aaaad36b4dcfc4fbf1330eccd03f971a
ms.sourcegitcommit: d1527eb2d50156bf923f2a32ec3af9efc7fc4304
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2018
ms.locfileid: "48250349"
---
# <a name="atl-ole-db-provider-wizard"></a>ATL OLE DB 提供程序向导

此向导将创建构成的 OLE DB 访问接口的类。

> [!WARNING]
> 在 Visual Studio 2017 版本 15.9 此代码向导已弃用，将 Visual Studio 的未来版本中删除。 很少使用此向导。 ATL 和 MFC 的常规支持不受此向导中删除。 如果你想要共享您对此不推荐使用的反馈，请先完成[这项调查](https://www.surveymonkey.com/r/QDWKKCN)。 你的反馈对我们很重要。


## <a name="remarks"></a>备注

从 Visual Studio 2008 开始，此向导生成的注册脚本将注册其 COM 组件**HKEY_CURRENT_USER**而不是**HKEY_LOCAL_MACHINE**。 若要修改此行为，请设置**的所有用户注册组件**ATL 向导的选项。

下表描述了在 ATL OLE DB 提供程序向导的选项：

- **短名称**

   键入要创建的提供程序的短名称。 自动填充向导中的其他编辑框，将基于此处键入的内容。 如果需要，可以编辑其他名称框。

- **组件类**

   组件类的名称。 ProgID 名称将更改以匹配此名称。

- **特性化**

   此选项指定向导是否将创建使用属性或模板声明提供程序类。 在选择此选项，该向导使用特性而不是模板声明 （如果创建特性化的项目，这是默认选项）。 当清除此选项时，向导使用模板声明而不是属性 （如果您创建了非特性化项目，这是默认选项）。

   如果创建非特性化项目时选择此选项，向导将警告您项目将被转换为特性化项目，并询问您是否继续与否。

- **ProgID**

   ProgID 或编程标识符是你的应用程序可以使用而不是一个 GUID 的文本字符串。 ProgID 的名称采用以下格式*为 Projectname.Coclassname*。

- **Version**

   您的提供程序的版本号。 默认值为 1。

- **数据源类**

   数据源类，窗体 C 的名称*短名称*源。

- **数据源.h 文件**

   数据源类的标头文件。 可以编辑此文件的名称，或选择现有的头文件。

- **会话类**

   窗体 C 的会话类的名称*短名称*会话。

- **会话.h 文件**

   会话类的标头文件。 可以编辑此文件的名称，或选择现有的头文件。

- **命令类**

   命令类，窗体 C 的名称*短名称*命令。

- **命令.h 文件**

   命令类的标头文件。 此名称不能进行编辑，取决于行集标头文件的名称。

- **行集类**

   窗体 C 的行集类的名称*短名称*行集。

- **行集.h 文件**

   行集类的标头文件。 可以编辑此文件的名称，或选择现有的头文件。

- **行集.cpp 文件**

   提供程序的实现文件。 可以编辑此文件的名称，或选择现有的实现文件。

## <a name="see-also"></a>请参阅

[ATL OLE DB 访问接口](../../atl/reference/adding-an-atl-ole-db-provider.md)


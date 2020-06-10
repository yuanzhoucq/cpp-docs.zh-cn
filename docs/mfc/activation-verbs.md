---
title: 激活：谓词
ms.date: 11/04/2016
helpviewer_keywords:
- verbs [MFC]
- OLE [MFC], activation
- edit verb [MFC]
- activation [MFC], verbs
- OLE [MFC], editing
- Primary verb [MFC]
- OLE activation {MFC]
ms.assetid: eb56ff23-1de8-43ad-abeb-dc7346ba7b70
ms.openlocfilehash: 03edba0a4336fdc147ef6dd10c7a8154aca19d3a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616635"
---
# <a name="activation-verbs"></a>激活：谓词

本文介绍 OLE[激活](activation-cpp.md)中的主要角色和辅助谓词扮演的角色。

通常，通过双击嵌入项，用户可以对其进行编辑。 但是，某些项的行为并不相同。 例如，双击用录音机应用程序创建的项不会在单独的窗口中打开服务器;相反，它会播放声音。

此行为差异的原因是录音机项具有不同的 "主谓词"。 主谓词是用户双击 OLE 项时执行的操作。 对于大多数类型的 OLE 项，主要谓词是 "编辑"，用于启动创建该项的服务器。 对于某些类型的项，例如录音机项，主谓词将播放。

许多类型的 OLE 项仅支持一个谓词，编辑是最常见的一项。 但是，某些类型的项支持多个谓词。 例如，录音机项支持编辑为辅助谓词。

通常会打开另一个使用的谓词。 除了服务器应用程序在单独的窗口中启动之外，Open 谓词与 Edit 完全相同。 当容器应用程序或服务器应用程序不支持就地激活时，应使用此谓词。

选择项时，必须通过子菜单命令调用除主谓词以外的任何谓词。 此子菜单包含该项支持的所有谓词，并且通常通过 "**编辑**" 菜单上的 " *typename* **对象**" 命令访问。 有关*typename* **Object**命令的信息，请参阅文章[菜单和资源：容器添加](menus-and-resources-container-additions.md)。

Windows 注册数据库中列出了服务器应用程序支持的谓词。 如果用 Microsoft 基础类库编写服务器应用程序，则在启动服务器时，它将自动注册所有谓词。 否则，应在服务器应用程序的初始化阶段注册它们。 有关详细信息，请参阅[注册](registration.md)文章。

## <a name="see-also"></a>另请参阅

[激活](activation-cpp.md)<br/>
[容器](containers.md)<br/>
[服务器](servers.md)

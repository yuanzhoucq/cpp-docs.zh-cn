---
title: 激活： 谓词 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- verbs [MFC]
- OLE [MFC], activation
- edit verb [MFC]
- activation [MFC], verbs
- OLE [MFC], editing
- Primary verb [MFC]
- OLE activation {MFC]
ms.assetid: eb56ff23-1de8-43ad-abeb-dc7346ba7b70
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 63b21e4d7f40d87b35d2ea5650f86801294affaa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425712"
---
# <a name="activation-verbs"></a>激活：谓词

此文章介绍了 OLE 中的角色主要和次要谓词 play[激活](../mfc/activation-cpp.md)。

通常情况下，双击嵌入的项允许用户对其进行编辑。 但是，某些项目不支持这种方式。 例如，双击使用录音机应用程序创建的项不会打开服务器在单独的窗口;相反，它会播放声音。

此行为差异的原因是录音机项具有不同"主谓词。" 主谓词是当用户双击 OLE 项时执行的操作。 对于大多数类型的 OLE 项中，主谓词是编辑，将启动创建项的服务器。 对于某些类型的项，如录音机项主谓词是 Play。

许多类型的 OLE 项支持只有一个谓词，并编辑是最常见的一个。 但是，某些类型的项支持多个谓词。 例如，录音机会项支持编辑作为辅助谓词。

另一个常用的谓词为 Open。 动词 Open 等同于编辑，但在一个单独的窗口中启动服务器应用程序。 容器应用程序或服务器应用程序不支持就地激活时，应使用此谓词。

选择项时，主谓词以外的任何谓词必须调用通过子菜单命令。 此子菜单包含所有支持的项的谓词，并通常通过访问*typename* **对象**命令**编辑**菜单。 有关的信息*typename* **对象**命令，请参阅文章[菜单和资源： 容器添加](../mfc/menus-and-resources-container-additions.md)。

Windows 注册数据库中列出的服务器应用程序支持的谓词。 如果服务器应用程序使用 Microsoft 基础类库编写的它将在服务器启动时自动注册所有谓词。 否则，应在服务器应用程序的初始化阶段进行注册。 有关详细信息，请参阅文章[注册](../mfc/registration.md)。

## <a name="see-also"></a>请参阅

[激活](../mfc/activation-cpp.md)<br/>
[容器](../mfc/containers.md)<br/>
[服务器](../mfc/servers.md)


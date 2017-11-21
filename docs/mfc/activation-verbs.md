---
title: "激活： 谓词 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- verbs [MFC]
- OLE [MFC], activation
- edit verb [MFC]
- activation [MFC], verbs
- OLE [MFC], editing
- Primary verb [MFC]
- OLE activation {MFC]
ms.assetid: eb56ff23-1de8-43ad-abeb-dc7346ba7b70
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e528697c27d03131245e94e795119611314c8921
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="activation-verbs"></a>激活：谓词
此文章介绍了 OLE 中的角色主和辅助动词扮演[激活](../mfc/activation-cpp.md)。  
  
 通常情况下，双击嵌入的项允许用户对其进行编辑。 但是，某些项目不支持这种方式。 例如，双击随录音机应用程序创建的项不无法打开服务器在单独的窗口;相反，它播放声音。  
  
 这种行为差异的原因是录音机项具有不同"主谓词。" 主谓词是当用户双击 OLE 项时执行的操作。 对于大多数类型的 OLE 项中，主谓词是编辑，将启动创建项的服务器。 对于某些类型的项，如录音机项主谓词是 Play。  
  
 许多类型的 OLE 项支持只有一个谓词，并编辑是最常见。 但是，某些类型的项支持多个谓词。 例如，录音机项支持编辑作为次要谓词。  
  
 频繁使用的另一个谓词为打开。 动词 Open 等同于编辑，但在单独的窗口中启动服务器应用程序。 当容器应用程序或服务器应用程序不支持就地激活，则应使用此谓词。  
  
 选择项目时，必须通过子菜单命令调用主谓词以外的任何谓词。 此子菜单包含支持的项的所有谓词，并通常通过访问*typename* **对象**命令**编辑**菜单。 有关信息*typename* **对象**命令，请参阅文章[菜单和资源： 容器添加](../mfc/menus-and-resources-container-additions.md)。  
  
 Windows 注册数据库中列出了服务器应用程序支持的谓词。 如果服务器应用程序使用 Microsoft 基础类库编写的它将自动注册所有谓词时该服务器已启动。 如果没有，您应在服务器应用程序的初始化阶段期间注册它们。 有关详细信息，请参阅文章[注册](../mfc/registration.md)。  
  
## <a name="see-also"></a>另请参阅  
 [激活](../mfc/activation-cpp.md)   
 [容器](../mfc/containers.md)   
 [服务器](../mfc/servers.md)


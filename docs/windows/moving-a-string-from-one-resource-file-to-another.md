---
title: 将字符串从一个资源文件移动到另一个 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], moving between files
- resource script files [C++], moving strings
- string editing, moving strings between resources
- String editor [C++], moving strings between files
ms.assetid: 94f8ee81-9b4c-4788-ba95-68c58db38029
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c99b5640d2ea855ade7f3f39ba233b3e5ff2ef04
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318858"
---
# <a name="moving-a-string-from-one-resource-file-to-another-c"></a>将字符串从一个资源文件移动到另一个 （c + +）

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>若要将字符串从一个资源脚本文件移动到另一个

1. 在这两个.rc 文件中打开字符串表。 (有关详细信息，请参阅[查看资源在资源脚本文件之外的一个项目](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。)

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 右键单击你想要并选择的字符串**剪切**从快捷菜单。

3. 将光标放在目标**字符串编辑器**窗口。

4. 在你想要移动字符串.rc 文件中，右键单击并选择**粘贴**从快捷菜单。

   > [!NOTE]
   > 如果**ID**或**值**与某个现有的移动的字符串冲突**ID**或者**值**在目标文件中，任一**ID**或**值**的更改已移动的字符串。 如果存在具有相同的字符串**ID**，则**ID**的更改已移动的字符串。 如果存在具有相同的字符串**值**，则**值**的更改已移动的字符串。

有关将资源添加到托管项目 （项目面向公共语言运行时） 的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[演练： 本地化 Windows 窗体](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3\(v=vs.100\))。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[字符串编辑器](../windows/string-editor.md)  
[资源文件](../windows/resource-files-visual-studio.md)  
[自定义窗口布局](/visualstudio/ide/customizing-window-layouts-in-visual-studio)  
---
title: 如何： 指定资源的包含目录 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- directories [C++], specifying include paths for resources
- include files, specifying for resources
- resources [Visual Studio], including in projects
ms.assetid: d6a7c0f6-4810-4bb0-b4b7-7d2476a20ca2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e0b655713a378c859bb017f661022f86aa687ab6
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676427"
---
# <a name="how-to-specify-include-directories-for-resources"></a>如何：指定资源的包含目录

### <a name="to-specify-include-directories-for-a-specific-rc-file"></a>为特定 .rc 文件指定包含目录

1. 右键单击解决方案资源管理器中的.rc 文件并选择**属性**从快捷菜单。

2. 在中**属性页**对话框中，单击**资源**节点，在左窗格中，然后指定附加的包含目录**附加包含目录**属性。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index).NET Framework 开发人员指南中。 

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[“资源包括”对话框](../windows/resource-includes-dialog-box.md)  
[TN035：在 Visual C++ 中使用多个资源文件和头文件](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)  
[符号：资源标识符](../windows/symbols-resource-identifiers.md)  
[资源文件](../windows/resource-files-visual-studio.md)  
[资源编辑器](../windows/resource-editors.md)
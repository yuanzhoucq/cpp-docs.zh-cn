---
title: 资源包括对话框的 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resourceincludes
dev_langs:
- C++
helpviewer_keywords:
- Resource Includes dialog box
- rc files, changing storage
- symbol header files, changing
- compiling source code, including resources
- .rc files, changing storage
- symbol header files, read-only
- symbols, symbol header files
ms.assetid: 659a54e6-e416-4045-8411-798730ff4ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d11f3abdaa4f804f9916e7313d1a4338c29a7369
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015074"
---
# <a name="resource-includes-dialog-box"></a>“资源包括”对话框
可以使用**资源包括**对话框来修改在项目.rc 文件和所有中存储的所有资源的环境的正常工作安排[符号](../windows/symbols-resource-identifiers.md)在 Resource.h 中。  
  
 若要打开**资源包括**对话框中，右键单击.rc 文件中[资源视图](../windows/resource-view-window.md)，然后选择**资源包括**从快捷菜单。  
  
 **符号头文件**  
 允许更改头文件的名称，头文件是存储资源文件的符号定义的位置。 有关详细信息，请参阅[更改符号头文件的名称](../windows/changing-the-names-of-symbol-header-files.md)。  
  
 **只读符号指令**  
 允许包含含有编辑会话期间不应修改的符号的头文件。 例如，可以包括在多个项目间共享的符号文件。 此外也可以包括 MFC.h 文件。 有关详细信息，请参阅[包括共享 （只读） 或计算符号](../windows/including-shared-read-only-or-calculated-symbols.md)。  
  
 **编译时指令**  
 允许包括所创建的资源文件，并可从主资源文件中的资源分别进行编辑，包含编译时指令（比如那些有条件地包括资源的指令），或者包含自定义格式的资源。 此外可以使用**编译时指令框**包括标准 MFC 资源文件。 有关详细信息，请参阅[编译时包含资源](../windows/how-to-include-resources-at-compile-time.md)。  
  
> [!NOTE]
>  由标记.rc 文件中显示这些文本框中的项`TEXTINCLUDE 1`， `TEXTINCLUDE 2`，和`TEXTINCLUDE 3`分别。 有关详细信息，请参阅[TN035： 使用多个资源文件和使用 Visual c + + 头文件](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)。  
  
 对资源文件使用进行了更改后**资源包括**对话框中，你需要关闭.rc 文件并重新打开它以使更改生效。 有关详细信息，请参阅[编译时包含资源](../windows/how-to-include-resources-at-compile-time.md)。  
  
## <a name="requirements"></a>要求  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [如何： 指定资源的包含目录](../windows/how-to-specify-include-directories-for-resources.md)   
 [符号： 资源标识符](../windows/symbols-resource-identifiers.md)   
 [资源文件](../windows/resource-files-visual-studio.md)   
 [资源编辑器](../windows/resource-editors.md)
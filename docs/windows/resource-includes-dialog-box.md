---
title: "资源包括对话框中 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 610e970ad84c6c89d91182b7a61bb759112fcd7d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="resource-includes-dialog-box"></a>“资源包括”对话框
你可以使用**资源包括**对话框来修改环境的正常工作安排，将所有资源都存储在项目.rc 文件和所有[符号](../windows/symbols-resource-identifiers.md)Resource.h 中。  
  
 若要打开**资源包括**对话框中，右键单击.rc 文件中[资源视图](../windows/resource-view-window.md)，然后选择**资源包括**从快捷菜单。  
  
 **符号头文件**  
 允许更改头文件的名称，头文件是存储资源文件的符号定义的位置。 有关详细信息，请参阅[更改符号头文件的名称](../windows/changing-the-names-of-symbol-header-files.md)。  
  
 **只读符号指令**  
 允许包含含有编辑会话期间不应修改的符号的头文件。 例如，可以包括在多个项目间共享的符号文件。 此外也可以包括 MFC.h 文件。 有关详细信息，请参阅[包括共享 （只读） 或计算符号](../windows/including-shared-read-only-or-calculated-symbols.md)。  
  
 **编译时指令**  
 允许包括所创建的资源文件，并可从主资源文件中的资源分别进行编辑，包含编译时指令（比如那些有条件地包括资源的指令），或者包含自定义格式的资源。 还可以使用“编译时指令”框包括标准 MFC 资源文件。 有关详细信息，请参阅[在编译时包括资源](../windows/how-to-include-resources-at-compile-time.md)。  
  
> [!NOTE]
>  这些文本框中的项显示在.rc 文件中标记`TEXTINCLUDE 1`， `TEXTINCLUDE 2`，和`TEXTINCLUDE 3`分别。 有关详细信息，请参阅[TN035： 使用多个资源文件和使用 Visual c + + 标头文件](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)。  
  
 对资源文件使用进行了更改后**资源包括**对话框，你需要关闭.rc 文件，然后重新打开它以使更改生效。 有关详细信息，请参阅[在编译时包括资源](../windows/how-to-include-resources-at-compile-time.md)。  
  

  
## <a name="requirements"></a>惠?  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [如何： 指定资源的包含目录](../windows/how-to-specify-include-directories-for-resources.md)   
 [符号： 资源标识符](../windows/symbols-resource-identifiers.md)   
 [资源文件](../windows/resource-files-visual-studio.md)   
 [资源编辑器](../windows/resource-editors.md)
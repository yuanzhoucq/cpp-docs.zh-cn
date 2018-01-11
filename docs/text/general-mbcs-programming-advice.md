---
title: "常规 MBCS 编程建议 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _mbcs
dev_langs: C++
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
caps.latest.revision: "9"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8a09bfb9b30e279e8d0b7696055c1e54ac56bfae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="general-mbcs-programming-advice"></a>常规 MBCS 编程建议
使用以下提示：  
  
-   对于灵活性，使用运行时宏例如`_tcschr`和`_tcscpy`在可能的情况。 有关详细信息，请参阅[Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)。  
  
-   使用 C 运行时`_getmbcp`函数可获取有关当前代码页信息。  
  
-   不要重复使用字符串资源。 具体取决于目标语言中，给定的字符串可能具有不同的含义时转换。 例如，"文件"上应用程序的主菜单可以转换以不同的方式从"文件"对话框中的字符串。 如果你需要使用具有相同名称的多个字符串，每个使用不同的字符串 Id。  
  
-   你可能想要找出是否在 mbcs 的操作系统上运行你的应用程序。 为此，请设置一个标志，在程序启动;不要依赖于 API 调用。  
  
-   在设计对话框时，允许大约 30 %mbcs 转换的静态文本控件的末尾额外空间。  
  
-   因为某些字体并非适用于所有系统，则会为你的应用程序，选择字体时请小心。 例如，日语版本的 Windows 2000 不支持 Helvetica 字体。  
  
-   在选择的字体对话框时，使用[MS Shell Dlg](http://msdn.microsoft.com/library/windows/desktop/dd374112)而不是 MS Sans Serif 或 Helvetica。 MS Shell Dlg 将被替换为正确的字体由系统在创建对话框之前。 使用 MS Shell Dlg 可确保在地应对此字体的操作系统中的任何更改都自动将可用。 （MFC 替换 MS Shell Dlg DEFAULT_GUI_FONT 或 Windows 95、 Windows 98 和 Windows NT 4 上的系统字体因为这些系统不正确处理 MS Shell Dlg。）  
  
-   在设计你的应用程序时，决定哪些字符串可以进行本地化。 如果有疑问，假定任何给定的字符串将进行本地化。 在这种情况下，不要使用不能混合可以进行本地化的字符串。  
  
## <a name="see-also"></a>请参阅  
 [MBCS 编程提示](../text/mbcs-programming-tips.md)   
 [递增和递减指针](../text/incrementing-and-decrementing-pointers.md)
---
title: "定义助记键 （访问键） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- access keys [C++], adding
- keyboard shortcuts [C++], controls
- dialog box controls, mnemonics
- access keys [C++], checking
- mnemonics, checking for duplicate
- mnemonics
- mnemonics, dialog box controls
- keyboard shortcuts [C++], uniqueness checking
- Check Mnemonics command
- controls [C++], access keys
- access keys [C++]
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7f19e255b2c8b63558dfe178ccfd7a23f8992861
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="defining-mnemonics-access-keys"></a>定义助记键（访问键）
通常情况下，键盘用户输入的焦点从一个控件移到另一个在对话框中使用 TAB 键和箭头键。 但是，你可以定义允许用户通过按单个键来选择控件的访问密钥 （助记键或易于记住的名称）。  
  
### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>若要定义具有可见标题 （下压按钮、 复选框和单选按钮） 的控件的访问密钥  
  
1.  选择在对话框中的控件。  
  
2.  中[属性窗口](/visualstudio/ide/reference/properties-window)，请在**标题**属性，键入该控件，键入 and 符的新名称 (**&**) 前面要作为的字母该控件的访问密钥。 例如 `&Radio1`。  
  
3.  按**输入**。  
  
     在显示的标题，以指示访问键，例如，会出现下划线**R**adio1。  
  
### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>若要定义无可见标题控件的访问键  
  
1.  通过使用使控件的标题**静态文本**中控制[工具箱](/visualstudio/ide/reference/toolbox)。  
  
2.  在静态文本标题中，输入与号 (**&**) 所需的访问密钥作为的字母之前。  
  
3.  请确保静态文本控件紧接在之前其标记的 tab 键顺序的控件。  
  
 对话框中的所有访问键应都是唯一的。  
  
#### <a name="to-check-for-duplicate-access-keys"></a>若要检查重复的访问键  
  
1.  上**格式**菜单上，单击**检查助记键**。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](https://msdn.microsoft.com/library/f45fce5x.aspx)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](https://msdn.microsoft.com/library/xbx3z216.aspx)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](https://msdn.microsoft.com/library/h6270d0z.aspx)。  
  
### <a name="requirements"></a>要求  
 Win32  
  
## <a name="see-also"></a>另请参阅  
 [在对话框中的控件](../windows/controls-in-dialog-boxes.md)   
 [控件](../mfc/controls-mfc.md)


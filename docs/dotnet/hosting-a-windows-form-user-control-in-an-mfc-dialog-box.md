---
title: "承载 Windows 窗体用户控件在 MFC 对话框中 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: da8e8a54947b329fe36eea5c80bdc13ba5cdfa74
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>在 MFC 对话框中承载 Windows 窗体用户控件
MFC 作为一种特殊的 ActiveX 控件承载 Windows 窗体控件和使用 ActiveX 接口和属性和方法，与控件进行通信<xref:System.Windows.Forms.Control>类。 我们建议你使用.NET Framework 属性和方法来操作该控件。  
  
 显示与 MFC 一起使用的 Windows 窗体的示例应用，请参阅[MFC 和 Windows 窗体集成](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。  
  
> [!NOTE]
>  在当前版本中，`CDialogBar`对象不能承载 Windows 窗体控件。  
  
## <a name="in-this-section"></a>本节内容  
 [如何：创建用户控件并将它承载在对话框中](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)  
  
 [如何： 使用 Windows 窗体执行 DDX/DDV 数据绑定](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)  
  
 [如何：接收来自本机 C++ 类的 Windows 窗体事件](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)  
  
## <a name="reference"></a>参考  
 [CWinFormsControl 类](../mfc/reference/cwinformscontrol-class.md)&#124;[CDialog 类](../mfc/reference/cdialog-class.md)&#124;[CWnd 类](../mfc/reference/cwnd-class.md)&#124;<xref:System.Windows.Forms.Control>  
  
## <a name="see-also"></a>请参阅  
 [在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Windows 窗体 /MFC 编程差异](../dotnet/windows-forms-mfc-programming-differences.md)   
 [作为 MFC 视图承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)   
 [以 MFC 对话框的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
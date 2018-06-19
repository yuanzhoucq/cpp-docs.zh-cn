---
title: ActiveX 控件容器： 将 ActiveX 控件连接到成员变量 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 06a2b6a5ab17db7b512f1f44d2eda68169d71645
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333126"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>ActiveX 控件容器：将 ActiveX 控件连接到成员变量
通过 ActiveX 控件的控件容器应用程序访问此类控件最轻松的方式是将 ActiveX 控件与将包含此类控件的对话框类的成员变量关联。  
  
> [!NOTE]
>  这不是通过容器类访问嵌入控件的唯一方式，但足以实现本文目的。  
  
### <a name="adding-a-member-variable-to-the-dialog-class"></a>将成员变量添加到对话框类  
  
1.  从“类视图”中，右键单击主对话框类以打开快捷菜单。 例如 `CContainerDlg`。  
  
2.  从快捷菜单中，单击**添加**然后**添加变量**。  
  
3.  在添加成员变量向导中，单击**控制变量**。  
  
4.  在**控件 ID**列表框中，选择嵌入 ActiveX 控件的控件 ID。 例如 `IDC_CIRCCTRL1`。  
  
5.  在**变量名称**框中，输入一个名称。  
  
     例如 `m_circctl`。  
  
6.  单击**完成**以接受你的选择并退出添加成员变量向导。  
  
## <a name="see-also"></a>请参阅  
 [ActiveX 控件容器](../mfc/activex-control-containers.md)


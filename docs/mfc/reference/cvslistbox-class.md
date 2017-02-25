---
title: "CVSListBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CVSListBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CVSListBox class"
  - "CVSListBox::PreTranslateMessage method"
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CVSListBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CVSListBox` 选件类支持可编辑列表控件。  
  
## 语法  
  
```  
class CVSListBox : public CVSListBoxBase  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CVSListBox::CVSListBox](../Topic/CVSListBox::CVSListBox.md)|构造 `CVSListBox` 对象。|  
|`CVSListBox::~CVSListBox`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CVSListBox::AddItem](../Topic/CVSListBox::AddItem.md)|添加一个字符串添加到列表控件。  （重写 `CVSListBoxBase::AddItem`。）|  
|[CVSListBox::EditItem](../Topic/CVSListBox::EditItem.md)|开始在列表控件项的文本的编辑操作。  （重写 `CVSListBoxBase::EditItem`。）|  
|[CVSListBox::GetCount](../Topic/CVSListBox::GetCount.md)|检索字符串的数量用在可编辑的列表控件。  （重写 `CVSListBoxBase::GetCount`。）|  
|[CVSListBox::GetItemData](../Topic/CVSListBox::GetItemData.md)|检索与可编辑列表控件项的一个特定的32位值。  （重写 `CVSListBoxBase::GetItemData`。）|  
|[CVSListBox::GetItemText](../Topic/CVSListBox::GetItemText.md)|检索文本编辑器可以列出控件项目。  （重写 `CVSListBoxBase::GetItemText`。）|  
|[CVSListBox::GetSelItem](../Topic/CVSListBox::GetSelItem.md)|检索当前选定项的从零开始的索引。可编辑的列表控件。  （重写 `CVSListBoxBase::GetSelItem`。）|  
|`CVSListBox::PreTranslateMessage`|在将调度到 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows功能之前，将windows消息。  有关更多信息和方法语法，请参见 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)。  （重写 `CVSListBoxBase::PreTranslateMessage`。）|  
|[CVSListBox::RemoveItem](../Topic/CVSListBox::RemoveItem.md)|从可编辑移除项列表控件。  （重写 `CVSListBoxBase::RemoveItem`。）|  
|[CVSListBox::SelectItem](../Topic/CVSListBox::SelectItem.md)|选择可编辑列表控制字符串。  （重写 `CVSListBoxBase::SelectItem`。）|  
|[CVSListBox::SetItemData](../Topic/CVSListBox::SetItemData.md)|将一个特定的32位值可编辑对象列表控件项目。  （重写 `CVSListBoxBase::SetItemData`。）|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CVSListBox::GetListHwnd](../Topic/CVSListBox::GetListHwnd.md)|返回的句柄嵌入的当前列表视图控件。|  
  
## 备注  
 `CVSListBox` 选件类提供设置编辑器在列表控件使用户创建，修改，删除或重新排列项的按钮。  
  
 下面是图片可编辑列表控件。  第二个列表项，标题为“和”，进行编辑。选择。  
  
 ![CVSListBox 控件](../../mfc/reference/media/cvslistbox.png "cvslistbox")  
  
 如果使用资源编辑器添加可编辑列表控件，通知编辑器中 **工具箱** 窗格不提供预定义的可编辑列表控件。  另外，请将静态控件\(如 **分组框** 控件。  框架使用静态控件作为占位符指定大小，并且位置可编辑列表控件。  
  
 若要使用可编辑列表在对话框模板的控件，声明在对话框选件类的一个 `CVSListBox` 变量。  为了支持数据交换了变量和控件之间，请定义在对话框中 `DoDataExchange` 方法的 `DDX_Control` 宏项。  默认情况下，可编辑列表控件创建不带编辑按钮。  使用继承的 [CVSListBoxBase::SetStandardButtons](http://msdn.microsoft.com/zh-cn/129e530f-97e9-42eb-b128-371c2a5686ba) 方法允许编辑按钮。  
  
 有关更多信息，请参见示例目录、 `New Controls` 示例，Page3.cpp和Page3.h文件。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CStatic](../../mfc/reference/cstatic-class.md)  
  
 `CVSListBoxBase`  
  
 [CVSListBox](../../mfc/reference/cvslistbox-class.md)  
  
## 要求  
 **标头:** afxvslistbox.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)
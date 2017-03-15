---
title: "MFC ActiveX 控件：高级主题 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FireError 方法"
  - "MFC ActiveX 控件, 访问不可见对话框控件"
  - "MFC ActiveX 控件, 高级主题"
  - "MFC ActiveX 控件, 数据库类"
  - "MFC ActiveX 控件, 错误代码"
  - "MFC ActiveX 控件, 参数化属性"
  - "MFC ActiveX 控件, 特殊键"
  - "PreTranslateMessage 方法"
  - "ThrowError 方法"
ms.assetid: e9e34abb-8e2d-461e-bb9c-a1aec5dcecbd
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# MFC ActiveX 控件：高级主题
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文包含高级主题与开发 ActiveX 控件。  这些元素包括：  
  
-   [使用在 ActiveX 控件的数据库类](#_core_using_database_classes_in_activex_controls)  
  
-   [实现参数化的属性](#_core_implementing_a_parameterized_property)  
  
-   [在 ActiveX 控件中的错误处理](#_core_handling_errors_in_your_activex_control)  
  
-   [处理在控件的特殊键](#_core_handling_special_keys_in_your_control)  
  
-   [访问在运行时不可见的对话框控件](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)  
  
##  <a name="_core_using_database_classes_in_activex_controls"></a> 使用在 ActiveX 控件的数据库类  
 由于 ActiveX 控件类是类库的一部分，您可应用相同过程和规则使用数据库类在标准 MFC 应用程序开发到使用 MFC 数据库类的 ActiveX 控件。  
  
 有关 MFC 数据库类的一般概述，请参见 [MFC 数据库类 DAO 和 ODBC \(\)](../data/mfc-database-classes-odbc-and-dao.md)。  文章介绍 MFC ODBC 类也适用于 MFC DAO 类并处理您可以在其中任何一种字符的更多详细信息。  
  
> [!NOTE]
>  从 Visual C\+\+ .NET 起，Visual C\+\+ 环境和向导不再支持 DAO（不过提供了 DAO 类，仍可供您使用）。  Microsoft 建议对新项目使用 [OLE DB 模板](../data/oledb/ole-db-programming.md) 或 [ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)。  DAO 只应用于维护现有的应用程序。  
  
##  <a name="_core_implementing_a_parameterized_property"></a> 实现参数化的属性  
 参数化的属性 \(有时调用属性数组\) 是的值公开的同类集合的方法为控件的单个属性。  例如，您可以使用之类参数化属性将公开数组或字典为属性。  使用数组表示法，在 Visual Basic 中，此类属性访问：  
  
 [!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/VisualBasic/mfc-activex-controls-advanced-topics_1.vb)]  
  
 使用添加属性向导实现参数化的属性。  添加属性向导通过将对实现属性允许用户使用控件访问属性的表示法或标准方式工作的 get\/set 函数。  
  
 类似于方法和属性，参数化的属性还具有一个限制。允许参数的数目。  对于参数化属性，限制为 15 个参数 \(其中一个用于存储属性值保留\)。  
  
 下面过程添加参数化的属性，调用数组，可以访问为一个二维整数数组。  
  
#### 使用"添加属性向导，添加参数化的属性  
  
1.  加载控件的项目。  
  
2.  在"类视图，展开控件的库节点。  
  
3.  右击控件 \(库节点的第二个节点接口节点\) 打开快捷菜单。  
  
4.  从快捷菜单中单击 **添加**，然后单击 **添加属性**。  
  
5.  在 **属性名** 框中，键入 `Array`。  
  
6.  在 **属性类型** 框中，选择 **short**。  
  
7.  对于 **实现** 类型，单击 **Get\/Set Methods**。  
  
8.  在 **Get Function** 和 **设置函数** 框中，键入一个唯一名称。get 和 set 函数或接受默认名称。  
  
9. 参数添加，调用 `row` \( `short`类型\)，使用 **参数名称** 并 **参数类型** 控件。  
  
10. 将第二个参数调用 `column` \( `short`类型\)。  
  
11. 单击**“完成”**。  
  
### 添加属性向导所做的更改  
 将自定义属性添加属性向导时，对类的更改 \(标题控件 H\) 和实现 \(.cpp\) 文件。  
  
 下列代码行添加到控件。H 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/CPP/mfc-activex-controls-advanced-topics_2.h)]  
  
 此代码声明允许用户申请特定行和列时，访问属性时的两个函数调用 `GetArray` 和 `SetArray`。  
  
 此外，添加属性向导添加下列代码行添加到控件映射计划，位于控件类实现 \(.cpp\) 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/CPP/mfc-activex-controls-advanced-topics_3.cpp)]  
  
 最后，`GetArray` 的实现和 `SetArray` 函数被添加到 .cpp 文件的结尾。  在许多情况下，您将修改获取函数返回属性值。  集合函数通常将包含应执行的代码，或者一，在属性更改之前。  
  
 对于这是有用的属性，可以声明在控件类的二维数组成员变量，**short**类型，为参数化的属性存储值。  然后可以修改获取函数返回值存储在相应的行和列表示的，这由参数，然后修改集合函数更新行和列参数引用的值。  
  
##  <a name="_core_handling_errors_in_your_activex_control"></a> 在 ActiveX 控件中的错误处理  
 如果错误状态控件中发生错误，则可能需要移动到控件容器报告。  具有报告错误的两种方法，根据错误的情况。  如果错误在属性的 get 或设置函数中，或放在一个 OLE 自动化方法的实现中，控件应当调用 [COleControl::ThrowError](../Topic/COleControl::ThrowError.md)，指示为控件用户发生错误。  如果错误在 \+ 其他 \+ 时候生成，控件应当调用 [COleControl::FireError](../Topic/COleControl::FireError.md)，触发一个库存错误事件。  
  
 若要指示发生的此错误，错误代码传递控件必须为 `ThrowError` 或 `FireError`。  错误代码是一个 OLE 状态代码，有 32 位值。  如果可能，请选择从标准错误代码。OLECTL.H 头文件中定义的代码。  下表总结了这些代码。  
  
### ActiveX 控件错误代码  
  
|错误|说明|  
|--------|--------|  
|**CTL\_E\_ILLEGALFUNCTIONCALL**|非法的函数调用|  
|**CTL\_E\_OVERFLOW**|溢出|  
|**CTL\_E\_OUTOFMEMORY**|内存不足|  
|**CTL\_E\_DIVISIONBYZERO**|被零除|  
|**CTL\_E\_OUTOFSTRINGSPACE**|字符串空间不足|  
|**CTL\_E\_OUTOFSTACKSPACE**|堆栈空间不足|  
|**CTL\_E\_BADFILENAMEORNUMBER**|文件名或编号无效|  
|**CTL\_E\_FILENOTFOUND**|未找到文件|  
|**CTL\_E\_BADFILEMODE**|错误文件"模式|  
|**CTL\_E\_FILEALREADYOPEN**|已打开的文件|  
|**CTL\_E\_DEVICEIOERROR**|设备 I\/O 错误|  
|**CTL\_E\_FILEALREADYEXISTS**|文件已存在|  
|**CTL\_E\_BADRECORDLENGTH**|错误记录长度|  
|**CTL\_E\_DISKFULL**|磁盘已满|  
|**CTL\_E\_BADRECORDNUMBER**|错误记录数|  
|**CTL\_E\_BADFILENAME**|文件名错误|  
|**CTL\_E\_TOOMANYFILES**|许多文件|  
|**CTL\_E\_DEVICEUNAVAILABLE**|没有的设备|  
|**CTL\_E\_PERMISSIONDENIED**|拒绝的权限|  
|**CTL\_E\_DISKNOTREADY**|未就绪的磁盘|  
|**CTL\_E\_PATHFILEACCESSERROR**|路径或文件访问错误|  
|**CTL\_E\_PATHNOTFOUND**|找不到路径|  
|**CTL\_E\_INVALIDPATTERNSTRING**|无效的模式字符串|  
|**CTL\_E\_INVALIDUSEOFNULL**|使用空的无效用法|  
|**CTL\_E\_INVALIDFILEFORMAT**|文件无效格式|  
|**CTL\_E\_INVALIDPROPERTYVALUE**|无效的属性值|  
|**CTL\_E\_INVALIDPROPERTYARRAYINDEX**|无效的属性数组索引|  
|**CTL\_E\_SETNOTSUPPORTEDATRUNTIME**|集不支持运行时|  
|**CTL\_E\_SETNOTSUPPORTED**|不支持的 \(只读的\) 属性集|  
|**CTL\_E\_NEEDPROPERTYARRAYINDEX**|需要数组索引属性|  
|**CTL\_E\_SETNOTPERMITTED**|未授予的权限集|  
|**CTL\_E\_GETNOTSUPPORTEDATRUNTIME**|获取未在运行时支持|  
|**CTL\_E\_GETNOTSUPPORTED**|不支持的。获取 \(只写属性\)|  
|**CTL\_E\_PROPERTYNOTFOUND**|找不到的属性|  
|**CTL\_E\_INVALIDCLIPBOARDFORMAT**|无效格式剪贴板|  
|**CTL\_E\_INVALIDPICTURE**|无效的图片|  
|**CTL\_E\_PRINTERERROR**|打印机错误|  
|**CTL\_E\_CANTSAVEFILETOTEMP**|无法保存文件为 TEMP|  
|**CTL\_E\_SEARCHTEXTNOTFOUND**|搜索找不到的文本|  
|**CTL\_E\_REPLACEMENTSTOOLONG**|替换太长|  
  
 如有必要，可使用 **CUSTOM\_CTL\_SCODE** 宏定义不受某个标准代码中的条件的自定义错误代码。  此宏的参数应是介于 1000 和 32767 之间的整数，包含。  例如：  
  
 [!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/CPP/mfc-activex-controls-advanced-topics_4.cpp)]  
  
 如果创建 ActiveX 控件替换现有 VBX 控件中，定义具有 VBX 控件确保使用相同的数值的 ActiveX 控件错误代码错误代码交互。  
  
##  <a name="_core_handling_special_keys_in_your_control"></a> 处理在控件的特殊键  
 有时您可能希望处理某些按键组合以特定方式；例如，请插入新行，必要时 Enter 键被按下一个多行 TextBox 控件或将在编辑一组控件之间时，一定向按 ID 密钥的。  
  
 如果 ActiveX 控件的基类是 `COleControl`，您可以重写处理消息，则容器处理它们。[CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md) 在使用此技术，总是返回 **TRUE** 时，如果处理 `PreTranslateMessage`重写的消息。  
  
 下面的代码示例演示处理所有消息。定向键关联的一种可能的方法。  
  
 [!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/CPP/mfc-activex-controls-advanced-topics_5.cpp)]  
  
 有关处理的更多信息键盘为 ActiveX 控件连接 ActiveX，请参见 SDK 文档。  
  
##  <a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a> 访问在运行时不可见的对话框控件  
 可以创建没有用户界面并在运行时不可见的对话框控件。  如果添加了在运行时不可见 ActiveX 控件添加到对话框并使用 [CWnd::GetDlgItem](../Topic/CWnd::GetDlgItem.md) 访问控件，控件将无法正常工作。  相反，应使用以下技术之一获取表示的控件对象：  
  
-   使用"添加成员变量向导 **控件变量 \(O\)**，然后选择 . 控件的 ID  输入成员变量的名称并选择控件的包装类定义为 **控件类型**。  
  
     \- 或 \-  
  
-   声明局部变量和子类以对话框项。  插入与下面类似的代码。`CMyCtrl` 是包装类，为 `IDC_MYCTRL1` 控件的 ID\):  
  
     [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/CPP/mfc-activex-controls-advanced-topics_6.cpp)]  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)
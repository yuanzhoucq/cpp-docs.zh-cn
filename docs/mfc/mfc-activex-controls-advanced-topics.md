---
title: "MFC ActiveX 控件： 高级主题 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- MFC ActiveX controls [MFC], accessing invisible dialog controls
- MFC ActiveX controls [MFC], advanced topics
- FireError method [MFC]
- MFC ActiveX controls [MFC], database classes
- MFC ActiveX controls [MFC], special keys
- PreTranslateMessage method [MFC]
- MFC ActiveX controls [MFC], parameterized property
- ThrowError method [MFC]
ms.assetid: e9e34abb-8e2d-461e-bb9c-a1aec5dcecbd
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 043c3307ed2729740cf973119264eb21d62a7a2b
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="mfc-activex-controls-advanced-topics"></a>MFC ActiveX 控件：高级主题
本文介绍如何与相关的开发 ActiveX 控件的高级的主题。 这些方法包括：  
  
-   [ActiveX 控件中使用数据库类](#_core_using_database_classes_in_activex_controls)  
  
-   [实现的参数化的属性](#_core_implementing_a_parameterized_property)  
  
-   [处理 ActiveX 控件中的错误](#_core_handling_errors_in_your_activex_control)  
  
-   [处理控件中的特殊键](#_core_handling_special_keys_in_your_control)  
  
-   [访问在运行时不可见的对话框控件](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)  
  
##  <a name="_core_using_database_classes_in_activex_controls"></a>ActiveX 控件中使用数据库类  
 因为 ActiveX 控件类是类库的一部分，所以可以应用相同的过程和使用数据库类开发 ActiveX 控件使用 MFC 数据库类一个标准 MFC 应用程序中的规则。  
  
 MFC 数据库类的一般概述，请参阅[MFC 数据库类 （DAO 和 ODBC）](../data/mfc-database-classes-odbc-and-dao.md)。 文章还介绍了 MFC ODBC 类和 MFC DAO 类，并将你定向到两边的更多详细信息。  
  
> [!NOTE]
>  Visual c + + 环境和向导不支持 DAO （尽管 DAO 类包括并且仍可以使用它们）。 Microsoft 建议你使用[OLE DB 模板](../data/oledb/ole-db-programming.md)或[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)为新项目。 你只应在维护现有应用程序使用 DAO。  
  
##  <a name="_core_implementing_a_parameterized_property"></a>实现的参数化的属性  
 参数化的属性 （有时称为的属性数组） 是用于公开作为控件的单个属性的值同类集合的方法。 例如，可以使用参数化的属性来公开一个数组或作为属性的字典。 在 Visual Basic 中，使用数组表示法访问此类属性：  
  
 [!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]  
  
 使用添加属性向导来实现的参数化的属性。 添加属性向导实现的方法将对允许控制用户访问使用上面的表示法的属性的 Get/Set 函数或标准的方式添加的属性。  
  
 类似于方法和属性，参数化属性还可以限制允许使用的参数数目。 在参数化属性的情况下限制为 15 个参数 （使用保留用于存储的属性值的一个参数）。  
  
 下面的过程添加名为数组，可作为一个二维的整数数组访问的参数化的属性。  
  
#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>若要添加使用添加属性向导的参数化的属性  
  
1.  加载控件的项目。  
  
2.  在“类视图”中，展开控件的库节点。  
  
3.  右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。  
  
4.  从快捷菜单中，单击**添加**，然后单击**添加属性**。  
  
5.  在**属性名称**框中，键入`Array`。  
  
6.  在**属性类型**框中，选择**短**。  
  
7.  有关**实现**类型，单击**Get/Set 方法**。  
  
8.  在**获取函数**和**设置函数**框中，为 Get 和 Set 函数键入唯一名称，或接受默认名称。  
  
9. 添加名为的参数`row`(类型`short`)，并使用**参数名称**和**参数类型**控件。  
  
10. 添加名为的第二个参数`column`(类型`short`)。  
  
11. 单击 **“完成”**。  
  
### <a name="changes-made-by-the-add-property-wizard"></a>所做的更改添加属性向导  
 当你添加自定义属性时，添加属性向导对控件类标头进行更改 (。H） 和实现 (。CPP) 文件。  
  
 将以下行添加到控件类。H 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]  
  
 此代码声明了两个函数调用`GetArray`和`SetArray`，允许用户访问该属性时请求的特定行和列。  
  
 此外，添加属性向导将以下行添加到控件调度映射，位于控件类实现 (。CPP) 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]  
  
 最后的实现`GetArray`和`SetArray`函数添加到的末尾。CPP 文件。 在大多数情况下，你将要修改 Get 函数以返回属性的值。 Set 函数通常将包含之前或在属性更改后应执行的代码。  
  
 为此属性才有用，可以声明类型的控件类中的二维数组成员变量**短**，以存储的参数化属性的值。 无法修改的 Get 函数中返回存储在正确的行和列的值，这些参数，所述，随后可修改的 Set 函数中更新引用由行和列的参数的值。  
  
##  <a name="_core_handling_errors_in_your_activex_control"></a>处理 ActiveX 控件中的错误  
 如果控件中出现错误条件，你可能需要将错误报告给控件容器。 有两种方法来报告错误，具体取决于发生错误情况。 如果发生错误的属性中获取或设置函数，或在 OLE 自动化方法的实现，该控件应调用[colecontrol:: Throwerror](../mfc/reference/colecontrol-class.md#throwerror)，出现错误控制用户的通知。 如果在其他任何时间发生错误，应调用控件[COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror)，这触发常用的错误事件。  
  
 若要指示已发生错误的种类，控件必须传递到的错误代码`ThrowError`或`FireError`。 错误代码是 OLE 状态代码，具有 32 位值。 如果可能，错误代码从标准集中选择 OLECTL 中定义的代码。H 标头文件。 下表总结了这些代码。  
  
### <a name="activex-control-error-codes"></a>ActiveX 控件错误代码  
  
|错误|描述|  
|-----------|-----------------|  
|**CTL_E_ILLEGALFUNCTIONCALL**|非法函数调用|  
|**CTL_E_OVERFLOW**|溢出|  
|**CTL_E_OUTOFMEMORY**|内存不足|  
|**CTL_E_DIVISIONBYZERO**|被零除|  
|**CTL_E_OUTOFSTRINGSPACE**|字符串空间不足|  
|**CTL_E_OUTOFSTACKSPACE**|堆栈空间不足|  
|**CTL_E_BADFILENAMEORNUMBER**|错误的文件名或文件号|  
|**CTL_E_FILENOTFOUND**|找不到文件|  
|**CTL_E_BADFILEMODE**|错误的文件模式|  
|**CTL_E_FILEALREADYOPEN**|文件已打开|  
|**CTL_E_DEVICEIOERROR**|设备 I/O 错误|  
|**CTL_E_FILEALREADYEXISTS**|文件已存在|  
|**CTL_E_BADRECORDLENGTH**|错误的记录长度|  
|**CTL_E_DISKFULL**|磁盘已满|  
|**CTL_E_BADRECORDNUMBER**|错误的记录号|  
|**CTL_E_BADFILENAME**|错误的文件名称|  
|**CTL_E_TOOMANYFILES**|文件太多|  
|**CTL_E_DEVICEUNAVAILABLE**|设备不可用|  
|**CTL_E_PERMISSIONDENIED**|权限被拒绝|  
|**CTL_E_DISKNOTREADY**|磁盘未准备好|  
|**CTL_E_PATHFILEACCESSERROR**|路径/文件访问错误|  
|**CTL_E_PATHNOTFOUND**|找不到路径|  
|**CTL_E_INVALIDPATTERNSTRING**|无效模式字符串|  
|**CTL_E_INVALIDUSEOFNULL**|为 NULL 的使用无效|  
|**CTL_E_INVALIDFILEFORMAT**|文件格式无效|  
|**CTL_E_INVALIDPROPERTYVALUE**|无效的属性值|  
|**CTL_E_INVALIDPROPERTYARRAYINDEX**|无效的属性数组索引|  
|**CTL_E_SETNOTSUPPORTEDATRUNTIME**|运行时不支持设置。|  
|**CTL_E_SETNOTSUPPORTED**|不支持 Set 语句(只读属性)|  
|**CTL_E_NEEDPROPERTYARRAYINDEX**|需要属性数组索引|  
|**CTL_E_SETNOTPERMITTED**|不允许进行设置|  
|**CTL_E_GETNOTSUPPORTEDATRUNTIME**|运行时不支持 Get 语句|  
|**CTL_E_GETNOTSUPPORTED**|不支持 Get（只写属性）|  
|**CTL_E_PROPERTYNOTFOUND**|找不到属性|  
|**CTL_E_INVALIDCLIPBOARDFORMAT**|剪贴板格式无效|  
|**CTL_E_INVALIDPICTURE**|无效的图片|  
|**CTL_E_PRINTERERROR**|打印机错误|  
|**CTL_E_CANTSAVEFILETOTEMP**|无法将文件保存到 TEMP|  
|**CTL_E_SEARCHTEXTNOTFOUND**|未找到搜索文本|  
|**CTL_E_REPLACEMENTSTOOLONG**|替换内容太长|  
  
 如有必要，使用**CUSTOM_CTL_SCODE**宏来定义一个标准的代码未涵盖的条件的自定义错误代码。 为此宏参数应为介于 1000年之间的整数和 32767 之间 （含）。 例如:   
  
 [!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]  
  
 如果要创建要替换现有 VBX 控件的 ActiveX 控件，定义具有相同的数字值将 VBX 控件使用以确保兼容的错误代码你 ActiveX 控件错误代码。  
  
##  <a name="_core_handling_special_keys_in_your_control"></a>处理控件中的特殊键  
 在某些情况下你可能想要以特殊方式; 处理某些击键组合例如，当方向将插入新行时多行文本框中按 ENTER 键框控件或编辑的组之间移动控制密钥按下的 ID。  
  
 如果 ActiveX 控件的基类是`COleControl`，您可以重写[cwnd:: Pretranslatemessage](../mfc/reference/cwnd-class.md#pretranslatemessage)容器处理它们之前处理消息。 在使用此方法时，始终返回**TRUE**如果的重写中处理消息`PreTranslateMessage`。  
  
 下面的代码示例演示了可能的处理的方向键与相关的任何消息。  
  
 [!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]  
  
 处理 ActiveX 控件的键盘界面的详细信息，请参阅 ActiveX SDK 文档。  
  
##  <a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a>访问在运行时不可见的对话框控件  
 你可以创建没有用户界面并在运行时不可见对话框控件。 如果将不可见的在运行时 ActiveX 控件添加到对话框中并使用[CWnd::GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem)若要访问控件，控件将无法正常工作。 相反，你应使用以下方法之一来获取表示控件的对象：  
  
-   使用添加成员变量向导选择**控制变量**，然后选择控件的 id。 输入一个成员变量名称并选择控件的包装类作为**控件类型**。  
  
     - 或 -  
  
-   为对话框项声明的局部变量和子类。 插入如下所示的代码 (`CMyCtrl`是包装器类，`IDC_MYCTRL1`是控件的 ID):  
  
     [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)


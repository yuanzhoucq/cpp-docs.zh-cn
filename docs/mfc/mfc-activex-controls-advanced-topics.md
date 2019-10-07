---
title: MFC ActiveX 控件：高级主题
ms.date: 09/12/2018
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
ms.openlocfilehash: e0daabf3d236eb7038f22c54ea76d616baf613a0
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096002"
---
# <a name="mfc-activex-controls-advanced-topics"></a>MFC ActiveX 控件：高级主题

本文介绍与开发 ActiveX 控件相关的高级主题。 这些问题包括：

- [在 ActiveX 控件中使用数据库类](#_core_using_database_classes_in_activex_controls)

- [实现参数化属性](#_core_implementing_a_parameterized_property)

- [处理 ActiveX 控件中的错误](#_core_handling_errors_in_your_activex_control)

- [处理控件中的特殊键](#_core_handling_special_keys_in_your_control)

- [访问运行时不可见的对话框控件](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX 是一种不能用于新开发的旧技术。 有关取代 ActiveX 的新式技术的详细信息，请参阅[Activex 控件](activex-controls.md)。

##  <a name="_core_using_database_classes_in_activex_controls"></a>在 ActiveX 控件中使用数据库类

由于 ActiveX 控件类是类库的一部分，因此可以应用相同的过程和规则，以便在标准 MFC 应用程序中使用数据库类来开发使用 MFC 数据库类的 ActiveX 控件。

有关 MFC 数据库类的一般概述，请参阅[Mfc 数据库类（DAO 和 ODBC）](../data/mfc-database-classes-odbc-and-dao.md)。 本文介绍 MFC ODBC 类和 MFC DAO 类，并指导您了解其中的任何一项。

> [!NOTE]
>   DAO 受 Office 2013 的支持。 DAO 3.6 是最终版本，被视为已过时。 视觉对象C++环境和向导不支持 dao （尽管包含 dao 类，但你仍可以使用它）。 Microsoft 建议你将[OLE DB 模板](../data/oledb/ole-db-programming.md)或[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)用于新项目。 只应在维护现有应用程序时使用 DAO。

##  <a name="_core_implementing_a_parameterized_property"></a>实现参数化属性

参数化属性（有时称为属性数组）是一个方法，用于将值的同类集合公开为控件的单个属性。 例如，可以使用参数化属性将数组或字典公开为属性。 在 Visual Basic 中，使用数组表示法访问此类属性：

[!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

使用添加属性向导实现参数化属性。 添加属性向导通过添加一对 Get/Set 函数来实现属性，这些函数允许控件用户使用以上表示法或标准方式访问属性。

与方法和属性类似，参数化属性也对允许的参数数目有限制。 对于参数化属性，限制为15个参数（为存储属性值保留一个参数）。

下面的过程添加了一个名为 Array 的参数化属性，该属性可作为二维整数数组进行访问。

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>使用 "添加属性向导" 添加参数化属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 在快捷菜单中，单击 "**添加**"，然后单击 "**添加属性**"。

1. 在 "**属性名称**" 框中`Array`，键入。

1. 在 "**属性类型**" 框中，选择**short**。

1. 对于 "**实现**类型"，请单击 " **Get/Set 方法**"。

1. 在**Get 函数**和**set 函数**框中，为 Get 和 set 函数键入唯一名称，或接受默认名称。

9. 使用**参数名称**和**参数类型**控件，添加一个名为*row* （类型为*short*）的参数。

10. 添加第二个名为*column*的参数（类型为*short*）。

11. 单击 **“完成”** 。

### <a name="changes-made-by-the-add-property-wizard"></a>添加属性向导所做的更改

添加自定义属性时，添加属性向导会更改控件类标头（。H）和实现（。CPP）文件。

将以下行添加到控件类中。H 文件：

[!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

此代码声明`SetArray`了两个`GetArray`名为的函数，使用户可以在访问属性时请求特定的行和列。

此外，"添加属性向导" 将以下行添加到控件调度映射，位于控件类实现（。CPP）文件：

[!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

最后，将`GetArray`和`SetArray`函数的实现添加到的末尾。CPP 文件。 在大多数情况下，你将修改 Get 函数以返回属性的值。 Set 函数通常包含应在属性更改之前或之后执行的代码。

若要使此属性有用，可以在类型为**short**的控件类中声明一个二维数组成员变量，以存储参数化属性的值。 然后，您可以修改 Get 函数以返回按参数所指示的正确行和列存储的值，然后修改 Set 函数以更新由 row 和 column 参数引用的值。

##  <a name="_core_handling_errors_in_your_activex_control"></a>处理 ActiveX 控件中的错误

如果控件中出现错误条件，则可能需要将错误报告给控件容器。 有两种报告错误的方法，具体取决于错误发生的情况。 如果错误发生在属性的 Get 或 Set 函数中，或在 OLE 自动化方法的实现中出现，则该控件应调用[COleControl：： ThrowError](../mfc/reference/colecontrol-class.md#throwerror)，它向控制用户发出错误已发生的信号。 如果在任何其他时间发生错误，控件应调用[COleControl：： FireError](../mfc/reference/colecontrol-class.md#fireerror)，这将激发 stock 错误事件。

若要指示发生的错误类型，控件必须将错误代码传递到`ThrowError`或。 `FireError` 错误代码是具有32位值的 OLE 状态代码。 如果可能，请从 OLECTL 中定义的标准代码集中选择错误代码。H 标头文件。 下表总结了这些代码。

### <a name="activex-control-error-codes"></a>ActiveX 控件错误代码

|Error|描述|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|非法的函数调用|
|CTL_E_OVERFLOW|溢出|
|CTL_E_OUTOFMEMORY|内存不足|
|CTL_E_DIVISIONBYZERO|被零除|
|CTL_E_OUTOFSTRINGSPACE|字符串空间不足|
|CTL_E_OUTOFSTACKSPACE|堆栈空间不足|
|CTL_E_BADFILENAMEORNUMBER|错误的文件名或文件号|
|CTL_E_FILENOTFOUND|找不到文件|
|CTL_E_BADFILEMODE|错误的文件模式|
|CTL_E_FILEALREADYOPEN|文件已打开|
|CTL_E_DEVICEIOERROR|设备 I/O 错误|
|CTL_E_FILEALREADYEXISTS|文件已存在|
|CTL_E_BADRECORDLENGTH|错误的记录长度|
|CTL_E_DISKFULL|磁盘已满|
|CTL_E_BADRECORDNUMBER|错误的记录号|
|CTL_E_BADFILENAME|错误的文件名|
|CTL_E_TOOMANYFILES|文件太多|
|CTL_E_DEVICEUNAVAILABLE|设备不可用|
|CTL_E_PERMISSIONDENIED|权限被拒绝|
|CTL_E_DISKNOTREADY|磁盘未准备好|
|CTL_E_PATHFILEACCESSERROR|路径/文件访问错误|
|CTL_E_PATHNOTFOUND|找不到路径|
|CTL_E_INVALIDPATTERNSTRING|无效模式字符串|
|CTL_E_INVALIDUSEOFNULL|NULL 的使用无效|
|CTL_E_INVALIDFILEFORMAT|文件格式无效|
|CTL_E_INVALIDPROPERTYVALUE|属性值无效|
|CTL_E_INVALIDPROPERTYARRAYINDEX|属性数组索引无效|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|运行时不支持设置。|
|CTL_E_SETNOTSUPPORTED|不支持 Set 语句(只读属性)|
|CTL_E_NEEDPROPERTYARRAYINDEX|需要属性数组索引|
|CTL_E_SETNOTPERMITTED|不允许进行设置|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|运行时不支持 Get 语句|
|CTL_E_GETNOTSUPPORTED|不支持 Get（只写属性）|
|CTL_E_PROPERTYNOTFOUND|找不到属性|
|CTL_E_INVALIDCLIPBOARDFORMAT|剪贴板格式无效|
|CTL_E_INVALIDPICTURE|图片无效|
|CTL_E_PRINTERERROR|打印机错误|
|CTL_E_CANTSAVEFILETOTEMP|无法将文件保存到 TEMP|
|CTL_E_SEARCHTEXTNOTFOUND|未找到搜索文本|
|CTL_E_REPLACEMENTSTOOLONG|替换内容太长|

如有必要，请使用 CUSTOM_CTL_SCODE 宏为某个标准代码未涵盖的条件定义自定义错误代码。 此宏的参数应为介于1000到32767（含）之间的整数。 例如：

[!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

如果要创建一个 ActiveX 控件来替换现有的 VBX 控件，请使用与 VBX 控件相同的数值来定义 ActiveX 控件错误代码，以确保错误代码兼容。

##  <a name="_core_handling_special_keys_in_your_control"></a>处理控件中的特殊键

在某些情况下，你可能想要以特殊方式处理某些击键组合;例如，在多行文本框控件中按 ENTER 键时插入新行，或在按下某个方向键 ID 时在一组编辑控件之间移动。

如果 ActiveX 控件的基类是`COleControl`，则可以重写[CWnd：:P retranslatemessage](../mfc/reference/cwnd-class.md#pretranslatemessage) ，以便在容器处理消息前处理这些消息。 使用此方法时，如果您在重写`PreTranslateMessage`中处理消息，则始终返回 TRUE。

下面的代码示例演示了一种可能的方法来处理与方向键相关的任何消息。

[!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

有关为 ActiveX 控件处理键盘接口的详细信息，请参阅 ActiveX SDK 文档。

##  <a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a>访问运行时不可见的对话框控件

您可以创建没有用户界面并且在运行时不可见的对话框控件。 如果在运行时 ActiveX 控件添加到对话框并使用[CWnd：： GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem)访问控件，则控件将无法正常工作。 相反，应使用以下方法之一来获取表示控件的对象：

- 使用 "添加成员变量" 向导，选择 "**控制变量**"，然后选择控件的 ID。 输入成员变量名称并选择控件的包装器类作为**控件类型**。

     或

- 将局部变量和子类声明为对话框项。 插入类似于以下内容的代码`CMyCtrl` （是包装类，IDC_MYCTRL1 是控件的 ID）：

   [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

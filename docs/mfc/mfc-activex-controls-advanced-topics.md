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
ms.openlocfilehash: c5e3be3915a0707f8df17d3c9ebe2eb0e4f623b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364631"
---
# <a name="mfc-activex-controls-advanced-topics"></a>MFC ActiveX 控件：高级主题

本文介绍与开发 ActiveX 控件相关的高级主题。 其中包括:

- [在 ActiveX 控件中使用数据库类](#_core_using_database_classes_in_activex_controls)

- [实现参数化属性](#_core_implementing_a_parameterized_property)

- [处理 ActiveX 控件中的错误](#_core_handling_errors_in_your_activex_control)

- [处理控件中的特殊密钥](#_core_handling_special_keys_in_your_control)

- [访问运行时不可见的对话框控件](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX 是一种不应用于新开发的传统技术。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

## <a name="using-database-classes-in-activex-controls"></a><a name="_core_using_database_classes_in_activex_controls"></a>在 ActiveX 控件中使用数据库类

由于 ActiveX 控件类是类库的一部分，因此可以应用相同的过程和规则，用于在标准 MFC 应用程序中使用数据库类来开发使用 MFC 数据库类的 ActiveX 控件。

有关 MFC 数据库类的概述，请参阅[MFC 数据库类 （DAO 和 ODBC）。](../data/mfc-database-classes-odbc-and-dao.md) 本文介绍了 MFC ODBC 类和 MFC DAO 类，并指导您了解这两个类的更多详细信息。

> [!NOTE]
> 通过 Office 2013 支持 DAO。 DAO 3.6 是最终版本，它被视为过时版本。 可视化C++环境和向导不支持 DAO（尽管包含 DAO 类，您仍可以使用它们）。 Microsoft 建议您将[OLE DB 模板](../data/oledb/ole-db-programming.md)或[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)用于新项目。 您只应在维护现有应用程序时使用 DAO。

## <a name="implementing-a-parameterized-property"></a><a name="_core_implementing_a_parameterized_property"></a>实现参数化属性

参数化属性（有时称为属性数组）是一种将值的同质集合公开为控件的单个属性的方法。 例如，可以使用参数化属性将数组或字典公开为属性。 在 Visual Basic 中，使用数组表示法访问此类属性：

[!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

使用添加属性向导实现参数化属性。 "添加属性向导"通过添加一对 Get/Set 函数来实现该属性，这些函数允许控件用户使用上述表示法或标准方式访问该属性。

与方法和属性类似，参数化属性也限制允许的参数数。 对于参数化属性，限制为 15 个参数（保留一个参数用于存储属性值）。

以下过程添加了一个参数化属性，称为 Array，可以作为整数的二维数组进行访问。

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>使用添加属性向导添加参数化属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 在快捷菜单中，单击"**添加**"，然后单击"**添加属性**"。

1. 在 **"属性名称"** 框中，`Array`键入 。

1. 在 **"属性类型"** 框中，选择 **"短**"。

1. 对于**实现**类型，单击 **"获取/设置方法**"。

1. 在 **"获取函数**和**设置函数"** 框中，为获取和设置函数键入唯一名称或接受默认名称。

1. 使用**参数名称**和**参数类型**控件添加参数，称为*行*（键入*短*）。

1. 添加第二个参数，称为*列*（键入*短*）。

1. 单击“完成”  。

### <a name="changes-made-by-the-add-property-wizard"></a>添加属性向导所做的更改

添加自定义属性时，"添加属性向导"会更改控件类标头 （。H） 和实现 （.CPP）文件。

以下行将添加到控件类 。H 文件：

[!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

此代码声明两个调用`GetArray`的函数`SetArray`，允许用户在访问属性时请求特定的行和列。

此外，添加属性向导将以下行添加到位于控件类实现 （） 中的控件调度映射中。CPP） 文件：

[!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

最后，将 和`GetArray``SetArray`函数的实现添加到 的末尾。CPP 文件。 在大多数情况下，您将修改 Get 函数以返回属性的值。 Set 函数通常包含应在属性更改之前或之后执行的代码。

为使此属性有用，可以在控件类（类型**short）** 中声明二维数组成员变量以存储参数化属性的值。 然后，您可以修改 Get 函数以返回存储在正确的行和列中的值（如参数所示），并修改 Set 函数以更新行和列参数引用的值。

## <a name="handling-errors-in-your-activex-control"></a><a name="_core_handling_errors_in_your_activex_control"></a>处理 ActiveX 控件中的错误

如果控件中出现错误条件，您可能需要向控制容器报告错误。 有两种方法可以报告错误，具体取决于发生错误的情况。 如果错误发生在属性的获取或设置函数中，或在 OLE 自动化方法的实现中发生，则控件应调用[COleControl：：throwError](../mfc/reference/colecontrol-class.md#throwerror)，该错误应向控件用户发出错误已发生信号。 如果错误发生在任何其他时间，控件应调用[COleControl：：FireError](../mfc/reference/colecontrol-class.md#fireerror)，这将触发库存错误事件。

要指示已发生的错误类型，控件必须将错误代码传递给`ThrowError`或`FireError`。 错误代码是 OLE 状态代码，具有 32 位值。 如果可能，请从 OLECTL 中定义的标准代码集中选择错误代码。H 头文件。 下表总结了这些代码。

### <a name="activex-control-error-codes"></a>ActiveX 控制错误代码

|错误|说明|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|非法函数调用|
|CTL_E_OVERFLOW|溢出|
|CTL_E_OUTOFMEMORY|内存不足|
|CTL_E_DIVISIONBYZERO|除零|
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
|CTL_E_BADFILENAME|文件名错误|
|CTL_E_TOOMANYFILES|文件太多|
|CTL_E_DEVICEUNAVAILABLE|设备不可用|
|CTL_E_PERMISSIONDENIED|权限被拒绝|
|CTL_E_DISKNOTREADY|磁盘未准备好|
|CTL_E_PATHFILEACCESSERROR|路径/文件访问错误|
|CTL_E_PATHNOTFOUND|找不到路径|
|CTL_E_INVALIDPATTERNSTRING|无效模式字符串|
|CTL_E_INVALIDUSEOFNULL|无效使用 NULL|
|CTL_E_INVALIDFILEFORMAT|无效的文件格式|
|CTL_E_INVALIDPROPERTYVALUE|无效属性值|
|CTL_E_INVALIDPROPERTYARRAYINDEX|无效属性数组索引|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|运行时不支持设置。|
|CTL_E_SETNOTSUPPORTED|不支持 Set 语句(只读属性)|
|CTL_E_NEEDPROPERTYARRAYINDEX|需要属性数组索引|
|CTL_E_SETNOTPERMITTED|不允许进行设置|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|运行时不支持 Get 语句|
|CTL_E_GETNOTSUPPORTED|不支持 Get（只写属性）|
|CTL_E_PROPERTYNOTFOUND|找不到属性|
|CTL_E_INVALIDCLIPBOARDFORMAT|无效剪贴板格式|
|CTL_E_INVALIDPICTURE|无效图片|
|CTL_E_PRINTERERROR|打印机错误|
|CTL_E_CANTSAVEFILETOTEMP|无法将文件保存到 TEMP|
|CTL_E_SEARCHTEXTNOTFOUND|未找到搜索文本|
|CTL_E_REPLACEMENTSTOOLONG|替换内容太长|

如有必要，请使用CUSTOM_CTL_SCODE宏为标准代码中未涵盖的条件定义自定义错误代码。 此宏的参数应介于 1000 和 32767 之间的整数（包括）。 例如：

[!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

如果要创建 ActiveX 控件以替换现有的 VBX 控件，请使用 VBX 控件使用相同的数值定义 ActiveX 控件错误代码，以确保错误代码兼容。

## <a name="handling-special-keys-in-the-control"></a><a name="_core_handling_special_keys_in_your_control"></a>处理控件中的特殊密钥

在某些情况下，您可能希望以特殊方式处理某些击键组合;例如，在多行文本框控件中按下 ENTER 键时插入新行，或在按下方向键 ID 时在一组编辑控件之间移动。

如果 ActiveX 控件的基类为`COleControl`，则可以重写[CWnd：:PreTranslateMessage，](../mfc/reference/cwnd-class.md#pretranslatemessage)在容器处理消息之前处理它们。 使用此技术时，如果在 重写 中处理消息，则始终返回`PreTranslateMessage`**TRUE。**

以下代码示例演示了处理与方向键相关的任何消息的可能方法。

[!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

有关为 ActiveX 控件处理键盘接口的详细信息，请参阅 ActiveX SDK 文档。

## <a name="accessing-dialog-controls-that-are-invisible-at-run-time"></a><a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a>访问运行时不可见的对话框控件

您可以创建没有用户界面并在运行时不可见的对话框控件。 如果在运行时将不可见的 ActiveX 控件添加到对话框中，并使用[CWnd：：GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem)访问该控件，则该控件将不能正常工作。 相反，应使用以下技术之一来获取表示控件的对象：

- 使用"添加成员变量向导"，选择 **"控制变量**"，然后选择控件的 ID。 输入成员变量名称，然后选择控件的包装类作为**控件类型**。

     -或-

- 将局部变量和子类声明为对话框项。 插入代码类似于以下内容（`CMyCtrl`包装类，IDC_MYCTRL1是控件的 ID）：

   [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)

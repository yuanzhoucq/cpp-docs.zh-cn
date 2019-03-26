---
title: 添加成员变量
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.member.variable
- vc.codewiz.variable.overview
helpviewer_keywords:
- member variables, adding
- member variables
- add member variable wizard [C++]
- dialog box controls, member variables
- dialog box controls, variable types
- variables, dialog box control member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
ms.openlocfilehash: 0f10b4867b443f0db69743d7ff23bb059290b0a5
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328956"
---
# <a name="add-a-member-variable"></a>添加成员变量

可使用“类视图”向类添加成员变量。 成员变量可以是[数据交换和数据验证](../mfc/dialog-data-exchange-and-validation.md)，也可以是泛型。 数据成员变量向导采用相关信息并使用其将元素插入源文件中的适当位置。 可从[资源视图](../windows/how-to-create-a-resource-script-file.md#create-resources)中的[对话框编辑器](../windows/dialog-editor.md)或[类视图](/visualstudio/ide/viewing-the-structure-of-code)添加成员变量。

> [!NOTE]
> 设计和实现对话框时，可能会发现使用对话框编辑器添加对话框控件，然后实现控件的成员变量更为有效。

**使用添加成员变量向导在资源视图中添加对话框控件的成员变量：**

1. 在资源视图中，展开项目节点和对话框节点，显示项目的对话框列表。

1. 双击要向其添加成员变量的对话框，在对话框编辑器中将其打开。

1. 在对话框编辑器中显示的对话框中，右键单击要向其添加成员变量的控件。

1. 在快捷菜单上，选择“添加变量”以显示[添加成员变量向导](#add-member-variable-wizard)。

   > [!NOTE]
   > “控件 ID”中已提供默认值。

1. 在相应向导框中提供信息。 有关详细信息，请参阅[对话框控件和变量类型](#dialog-box-controls-and-variable-types)。

1. 选择“完成”，即可将定义和实现代码添加到项目并关闭向导。

**使用添加成员变量向导从类视图中添加成员变量：**

1. 在[“类视图”](/visualstudio/ide/viewing-the-structure-of-code)中，展开项目节点，显示项目中的类。

1. 右键单击要向其添加变量的类。

1. 在快捷菜单上，选择“添加”，然后选择“添加变量”以显示添加成员变量向导。

1. 在相应向导框中提供信息。 有关详细信息，请参阅[添加成员变量向导](#add-member-variable-wizard)。

1. 选择“完成”，即可将定义和实现代码添加到项目并关闭向导。

## <a name="in-this-section"></a>本节内容

- [添加成员变量向导](#add-member-variable-wizard)
- [对话框控件和变量类型](#dialog-box-controls-and-variable-types)

## <a name="add-member-variable-wizard"></a>添加成员变量向导

此向导将成员变量声明添加到头文件中。 根据选项，它可将代码添加到 .cpp 文件。 如果使用此向导添加了成员变量，则可以在开发环境中编辑代码。

- **访问**

  设置成员变量的访问权限。 访问修饰符是一种关键字，用于指定其他类对该成员变量的访问权限。 有关指定访问权限的详细信息，请参阅[成员访问控制](../cpp/member-access-control-cpp.md)。 默认情况下，成员变量的访问级别设置为 `public`。

  - [public](../cpp/public-cpp.md)
  - [受保护](../cpp/protected-cpp.md)
  - [private](../cpp/private-cpp.md)

- **变量类型**

  设置要添加的成员变量的返回类型。

  - 如果要添加的成员变量不是对话框控件，请从可用类型列表中进行选择。

    有关类型的信息，请参阅[基础类型](../cpp/fundamental-types-cpp.md)。

    |||
    |-|-|
    |`char`|`short`|
    |`double`|`unsigned char`|
    |`float`|`unsigned int`|
    |`int`|`unsigned long`|
    |`long`||

  - 如果要添加一个对话框控件的成员变量，则此框填入控件或值的返回对象的类型。 如果选择“控件”，则“变量类型”指定在“控件 ID”框中选择的控件的基类。 如果对话框控件可以包含一个值，并且你选择了“值”，则“变量类型”指定控件可以包含的值的适当类型。 有关详细信息，请参阅[对话框控件和变量类型](#dialog-box-controls-and-variable-types)。

    此值取决于在“控件 ID”中所选的内容，且无法更改。

- **变量名**

  设置要添加的成员变量的名称。 成员变量通常以可识别的字符串 `m_` 开头，此字符串会作为默认内容提供。

- **控件变量**

  指示成员变量在具有[数据交换和数据验证](../mfc/dialog-data-exchange-and-validation.md)支持的对话框中管理控件。 有关详细信息，请参阅 [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)。 此选项仅能用于向派生自 [CDialog](../mfc/reference/cdialog-class.md) 的类添加的成员变量。 选择此框以激活“控件 ID”和“控件类型”选项。

- **控件 ID**

  为要添加的控件变量设置 ID。 从要为其添加成员变量的控件类型的 ID 列表中进行选择。 该列表仅在选中“控件变量”框时为活动状态，且仅包含已添加到对话框的控件 ID。 例如，对于标准的“确定”按钮，控件 ID 为“IDOK”。

  |选项|说明|
  |------------|-----------------|
  |**控件**|此选项为控件类型的默认设置选项。 它管理控件本身，而不管理控件的状态或内容（比如你可能希望管理列表框、组合框或编辑框）。|
  |**值**|此选项适用于可以保存值或显示状态的控件类型，例如编辑框或复选框。 此外，此选项也可于管理范围、内容或状态的控件类型。 有关详细信息，请参阅[对话框控件和变量类型](#dialog-box-controls-and-variable-types)。|

- **类别**

  指定变量基于控件类型还是控件的值。

- **控件类型**

  设置要添加的控件类型。 此框不可更改。 例如，按钮的控件类型为 BUTTON，而组合框的控件类型为 COMBOBOX。 有关详细信息，请参阅[对话框控件和变量类型](#dialog-box-controls-and-variable-types)。

- **最大字符数**

  仅当“变量类型”设为 [CString](../atl-mfc-shared/reference/cstringt-class.md) 时可用。 表示控件能容纳的最大字符数。

- **最小值**

  仅当变量类型为 `BOOL`、`int`、`UINT`、`long`、`DWORD`、`float`、`double`、`BYTE`、`short`、[COLECurrency](../mfc/reference/colecurrency-class.md) 或 [CTime](../atl-mfc-shared/reference/ctime-class.md) 时才可用。 表示规模或日期范围可接受的最小值。

- **最大值**

  仅当变量类型为 `BOOL`、`int`、`UINT`、`long`、`DWORD`、`float`、`double`、`BYTE`、`short`、`COLECurrency` 或 `CTime` 时才可用。 表示规模或日期范围可接受的最大值。

- **.h 文件**

  用于 ActiveX 控件，该控件的成员变量需要一个包装类。 设置头文件的名称以便添加类声明。

- **.cpp 文件**

  用于 ActiveX 控件，该控件的成员变量需要一个包装类。 设置实现文件的名词以便添加类声明。

- **注释**

  在成员变量的头文件中提供注释。

## <a name="dialog-box-controls-and-variable-types"></a>对话框控件和变量类型

可使用[添加成员变量向导](#add-member-variable-wizard)，将成员变量添加到使用 MFC 创建的对话框控件中。 为其添加成员变量的控件类型决定了对话框中显示的选项。

下表介绍了 MFC 和[对话框编辑器](../windows/dialog-editor.md)中支持的所有对话框控件类型。 此外，还显示了可用的类型和值。

|控件|控件类型|控件变量类型|值变量类型|最小值/最大值（仅限值类型）|
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|
|动画控件|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|无；仅控件|不可用|
|Button|BUTTON|[CButton](../mfc/reference/cbutton-class.md)|无；仅控件|不可用|
|复选框|CHECK|[CButton](../mfc/reference/cbutton-class.md)|`BOOL`|最小值/最大值|
|组合框|COMBOBOX|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|最大字符数|
|日期时间选择器控件|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime](../atl-mfc-shared/reference/ctime-class.md)|最小值/最大值|
|编辑框|编辑|[CEdit](../mfc/reference/cedit-class.md)|`CString`、int、UINT、long、DWORD、float、double、BYTE、short、BOOL、`COleDateTime` 或 `COleCurrency`|最小值/最大值；某些支持最大字符数|
|热键控件|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|无；仅控件|不可用|
|列表框|LISTBOX|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|最大字符数|
|列表控件|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|无；仅控件|不可用|
|月历控件|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|最小值/最大值|
|进度控件|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|无；仅控件|不可用|
|Rich Edit 2 控件|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|最大字符数|
|Rich Edit 控件|RICHEDIT|`CRichEditCtrl`|`CString`|最大字符数|
|滚动条（垂直或水平）|SCROLLBAR|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|最小值/最大值|
|Slider 控件|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|最小值/最大值|
|数值调节钮控件|msctls_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|无；仅控件|不可用|
|Tab 控件|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|无；仅控件|不可用|
|树控件|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|无；仅控件|不可用|

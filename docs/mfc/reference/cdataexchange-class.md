---
title: CDataExchange 类
ms.date: 11/04/2016
f1_keywords:
- CDataExchange
- AFXWIN/CDataExchange
- AFXWIN/CDataExchange::CDataExchange
- AFXWIN/CDataExchange::Fail
- AFXWIN/CDataExchange::PrepareCtrl
- AFXWIN/CDataExchange::PrepareEditCtrl
- AFXWIN/CDataExchange::PrepareOleCtrl
- AFXWIN/CDataExchange::m_bSaveAndValidate
- AFXWIN/CDataExchange::m_pDlgWnd
helpviewer_keywords:
- CDataExchange [MFC], CDataExchange
- CDataExchange [MFC], Fail
- CDataExchange [MFC], PrepareCtrl
- CDataExchange [MFC], PrepareEditCtrl
- CDataExchange [MFC], PrepareOleCtrl
- CDataExchange [MFC], m_bSaveAndValidate
- CDataExchange [MFC], m_pDlgWnd
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
ms.openlocfilehash: fd1bce7de7ac323dc3099ab4938306768eb95a35
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754630"
---
# <a name="cdataexchange-class"></a>CDataExchange 类

支持 Microsoft 基础类使用的对话框数据交换 (DDX) 和对话框数据验证 (DDV) 例程。

## <a name="syntax"></a>语法

```
class CDataExchange
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDataExchange：CDataExchange](#cdataexchange)|构造 `CDataExchange` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDataExchange：失败](#fail)|验证失败时调用。 将焦点重置为上一个控件并引发异常。|
|[CDataExchange：:P雷帕雷克拉尔](#preparectrl)|准备指定的控件以进行数据交换或验证。 用于非编辑控件。|
|[CDataExchange：:P回复编辑](#prepareeditctrl)|准备指定的编辑控件以进行数据交换或验证。|
|[CDataExchange：:P雷帕雷奥塞尔](#prepareolectrl)|准备指定的 OLE 控件以进行数据交换或验证。 用于非编辑控件。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CDataExchange：m_bSaveAndValidate](#m_bsaveandvalidate)|为 DDX 和 DDV 方向标记。|
|[CDataExchange：m_pDlgWnd](#m_pdlgwnd)|发生数据交换的对话框或窗口。|

## <a name="remarks"></a>备注

`CDataExchange`没有基类。

如果要为自定义数据类型或控件编写数据交换例程，或者编写自己的数据验证例程，请使用此类。 有关编写自己的 DDX 和 DDV 例程的详细信息，请参阅[技术说明 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)以及[对话框](../../mfc/dialog-boxes.md)。

对象`CDataExchange`提供发生 DDX 和 DDV 所需的上下文信息。 当 DDX 用于填充数据成员对话框控件的初始值时 *，标志m_bSaveAndValidate*为 FALSE。 当使用 DDX 将对话框控件的当前值设置为数据成员以及使用 DDV 验证数据值时，标志*m_bSaveAndValidate*为 TRUE。 如果 DDV 验证失败，DDV 过程将显示一个消息框，解释输入错误。 然后，DDV 过程将`Fail`调用将焦点重置为违规控件，并引发异常以停止验证过程。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CDataExchange`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cdataexchangecdataexchange"></a><a name="cdataexchange"></a>CDataExchange：CDataExchange

调用此成员函数以构造对象`CDataExchange`。

```
CDataExchange(
    CWnd* pDlgWnd,
    BOOL bSaveAndValidate);
```

### <a name="parameters"></a>参数

*普德格温德*<br/>
指向包含控件的父窗口的指针。 通常这是[CDialog](../../mfc/reference/cdialog-class.md)派生对象。

*b 保存和验证*<br/>
如果 TRUE，则此对象验证数据，然后将数据从控件写入成员。 如果 FALSE，此对象会将数据从成员移动到控件。

### <a name="remarks"></a>备注

自行构造`CDataExchange`一个对象，以将数据交换对象中存储额外信息以传递到窗口的[CWnd：:DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]

## <a name="cdataexchangefail"></a><a name="fail"></a>CDataExchange：失败

当对话框数据验证 （DDV） 操作失败时，框架将调用此成员函数。

```cpp
void Fail();
```

### <a name="remarks"></a>备注

`Fail`将焦点和选择还原到验证失败的控件（如果有要还原的控件）。 `Fail`然后引发[CUserException](../../mfc/reference/cuserexception-class.md)类型的异常以停止验证过程。 该异常会导致显示一个消息框，解释要显示的错误。 DDV 验证失败后，用户可以在违规控件中重新输入数据。

当验证失败时，自定义 DDV 例程`Fail`的实现者可以从其例程调用。

有关编写自己的 DDX 和 DDV 例程的详细信息，请参阅[技术说明 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)以及[对话框主题](../../mfc/dialog-boxes.md)。

## <a name="cdataexchangem_bsaveandvalidate"></a><a name="m_bsaveandvalidate"></a>CDataExchange：m_bSaveAndValidate

此标志指示对话框数据交换 （DDX） 操作的方向。

```
BOOL m_bSaveAndValidate;
```

### <a name="remarks"></a>备注

如果`CDataExchange`对象用于在用户编辑控件后将数据从对话框控件移动到对话框类数据成员，则该标志为非零。 如果对象用于从对话框类数据成员初始化对话框控件，则标志为零。

在对话框数据验证 （DDV） 期间，标志也是非零。

有关编写自己的 DDX 和 DDV 例程的详细信息，请参阅[技术说明 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)以及[对话框主题](../../mfc/dialog-boxes.md)。

## <a name="cdataexchangem_pdlgwnd"></a><a name="m_pdlgwnd"></a>CDataExchange：m_pDlgWnd

包含指向正在为其进行对话数据交换 （DDX） 或验证 （DDV） 的[CWnd](../../mfc/reference/cwnd-class.md)对象的指针。

```
CWnd* m_pDlgWnd;
```

### <a name="remarks"></a>备注

此对象通常是[CDialog](../../mfc/reference/cdialog-class.md)对象。 自定义 DDX 或 DDV 例程的实现者可以使用此指针获取对包含它们正在操作的控件的对话框窗口的访问。

有关编写自己的 DDX 和 DDV 例程的详细信息，请参阅[技术说明 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)以及[对话框主题](../../mfc/dialog-boxes.md)。

## <a name="cdataexchangepreparectrl"></a><a name="preparectrl"></a>CDataExchange：:P雷帕雷克拉尔

框架调用此成员函数以准备为对话框数据交换 （DDX） 和验证 （DDV） 指定的控件。

```
HWND PrepareCtrl(int nIDC);
```

### <a name="parameters"></a>参数

*nIDC*<br/>
要为 DDX 或 DDV 准备的控件的 ID。

### <a name="return-value"></a>返回值

为 DDX 或 DDV 准备的控件的 HWND。

### <a name="remarks"></a>备注

使用[准备编辑Ctrl](#prepareeditctrl)代替编辑控件;将此成员函数用于所有其他控件。

准备包括将控件的 HWND 存储在类中`CDataExchange`。 框架使用此句柄在 DDX 或 DDV 发生故障时将焦点还原到以前重点控件。

自定义 DDX 或 DDV 例程的实现者`PrepareCtrl`应调用所有非编辑控件，它们正在通过 DDX 交换数据或通过 DDV 验证数据。

有关编写自己的 DDX 和 DDV 例程的详细信息，请参阅[技术说明 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)以及[对话框主题](../../mfc/dialog-boxes.md)。

## <a name="cdataexchangeprepareeditctrl"></a><a name="prepareeditctrl"></a>CDataExchange：:P回复编辑

框架调用此成员函数以准备为对话框数据交换 （DDX） 和验证 （DDV） 指定的编辑控件。

```
HWND PrepareEditCtrl(int nIDC);
```

### <a name="parameters"></a>参数

*nIDC*<br/>
为 DDX 或 DDV 准备的编辑控件的 ID。

### <a name="return-value"></a>返回值

为 DDX 或 DDV 准备的编辑控件的 HWND。

### <a name="remarks"></a>备注

对所有非编辑控件使用[PrepareCtrl。](#preparectrl)

准备包括两件事。 首先，`PrepareEditCtrl`将控件的 HWND 存储在类`CDataExchange`中。 框架使用此句柄在 DDX 或 DDV 发生故障时将焦点还原到以前重点控件。 其次，`PrepareEditCtrl`在`CDataExchange`类中设置一个标志，以指示正在交换或验证其数据的控件是编辑控件。

自定义 DDX 或 DDV 例程的实现者`PrepareEditCtrl`应调用所有编辑控件，它们正在通过 DDX 交换数据或通过 DDV 验证数据。

有关编写自己的 DDX 和 DDV 例程的详细信息，请参阅[技术说明 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)以及[对话框主题](../../mfc/dialog-boxes.md)。

## <a name="cdataexchangeprepareolectrl"></a><a name="prepareolectrl"></a>CDataExchange：:P雷帕雷奥塞尔

框架调用此成员函数以准备为对话框数据交换 （DDX） 和验证 （DDV） 指定的 OLE 控件。

```
COleControlSite* PrepareOleCtrl(int nIDC);
```

### <a name="parameters"></a>参数

*nIDC*<br/>
为 DDX 或 DDV 准备的 OLE 控件的 ID。

### <a name="return-value"></a>返回值

指向 OLE 控制站点的指针。

### <a name="remarks"></a>备注

使用[准备编辑Ctrl](#prepareeditctrl)改为编辑控件或[准备Ctrl](#preparectrl)的所有其他非 OLE 控件。

自定义 DDX 或 DDV 例程的实现者`PrepareOleCtrl`应调用所有 OLE 控件，它们正在通过 DDX 交换数据或通过 DDV 验证数据。

有关编写自己的 DDX 和 DDV 例程的详细信息，请参阅[技术说明 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)以及[对话框主题](../../mfc/dialog-boxes.md)。

## <a name="see-also"></a>请参阅

[MFC 样品视图](../../overview/visual-cpp-samples.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CWnd：:DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)<br/>
[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)

---
title: CMFCDesktopAlertWndInfo 类
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_hIcon
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_nURLCmdID
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strText
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strURL
helpviewer_keywords:
- CMFCDesktopAlertWndInfo [MFC], m_hIcon
- CMFCDesktopAlertWndInfo [MFC], m_nURLCmdID
- CMFCDesktopAlertWndInfo [MFC], m_strText
- CMFCDesktopAlertWndInfo [MFC], m_strURL
ms.assetid: 5c9bb84e-6c96-4748-8e74-6951b6ae8e84
ms.openlocfilehash: f51c1b75e0c096a34b190e36e097aaca4109b5f8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367586"
---
# <a name="cmfcdesktopalertwndinfo-class"></a>CMFCDesktopAlertWndInfo 类

该`CMFCDesktopAlertWndInfo`类与[CMFC 桌面警报类](../../mfc/reference/cmfcdesktopalertwnd-class.md)一起使用。 它指定在桌面警报窗口弹出时显示的控件。

## <a name="syntax"></a>语法

```
class CMFCDesktopAlertWndInfo
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC桌面警报信息：：操作员*](#operator_eq)||

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CMFC桌面警报信息：：m_hIcon](#m_hicon)|显示的图标的句柄。|
|[CMFC 桌面警报信息：：m_nURLCmdID](#m_nurlcmdid)|与桌面警报窗口中的链接关联的命令 ID。|
|[CMFC桌面警报信息：：m_strText](#m_strtext)|桌面警报窗口中显示的文本。|
|[CMFC桌面警报信息：：m_strURL](#m_strurl)|桌面警报窗口中显示的链接。|

## <a name="remarks"></a>备注

类`CMFCDesktopAlertWndInfo`将传递给[CMFCDesktopAlertWnd：：创建](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)方法来指定桌面警报窗口的默认对话框中显示的元素。 默认对话框可以包含三个项目：

- 一个图标，它通过调用[CMFCDesktopAlertWndinfo：：m_hIcon](#m_hicon)设置。

- 标签或短信，通过调用[CMFCDesktopAlertWndinfo：m_strText](#m_strtext)设置。

- 链接，通过调用[CMFCDesktopAlertWndinfo：m_strURL](#m_strurl)设置。 要设置单击链接时执行的命令，请致电[CMFCDesktopAlertWndinfo：：m_nURLCmdID](#m_nurlcmdid)。

如果默认对话框不够，您可以创建自定义对话框并将其传递给[CMFCDesktopAlertWnd：：创建](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)方法，而不是使用此类。 有关详细信息，请参阅[CMFC 桌面警报对话类](../../mfc/reference/cmfcdesktopalertdialog-class.md)。

## <a name="example"></a>示例

下面的示例演示如何在`CMFCDesktopAlertWndInfo`类中使用各种成员。 该示例演示如何将句柄设置为显示的图标、桌面警报窗口中显示的文本、桌面警报窗口中显示的链接以及与桌面警报窗口中的链接关联的命令 ID。 此示例是[桌面警报演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)

## <a name="requirements"></a>要求

**标题：** afxDesktopAlertDialog.h

## <a name="cmfcdesktopalertwndinfooperator"></a><a name="operator_eq"></a>CMFC桌面警报信息：：操作员*

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```

### <a name="parameters"></a>参数

[在]*斯尔克*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcdesktopalertwndinfom_hicon"></a><a name="m_hicon"></a>CMFC桌面警报信息：：m_hIcon

显示的图标的句柄。

```
HICON m_hIcon;
```

### <a name="remarks"></a>备注

## <a name="cmfcdesktopalertwndinfom_nurlcmdid"></a><a name="m_nurlcmdid"></a>CMFC 桌面警报信息：：m_nURLCmdID

与桌面警报窗口中的链接关联的命令 ID。

```
UINT m_nURLCmdID;
```

### <a name="remarks"></a>备注

当用户单击[CMFCDesktopAlertWndinfo 指定的](#m_strurl)链接时，命令 ID 将发送给弹出窗口的所有者：m_strURL 。

## <a name="cmfcdesktopalertwndinfom_strtext"></a><a name="m_strtext"></a>CMFC桌面警报信息：：m_strText

桌面警报窗口中显示的文本。

```
CString m_strText;
```

### <a name="remarks"></a>备注

## <a name="cmfcdesktopalertwndinfom_strurl"></a><a name="m_strurl"></a>CMFC桌面警报信息：：m_strURL

桌面警报窗口中显示的链接。

```
CString m_strURL;
```

### <a name="remarks"></a>备注

当用户单击该链接时，具有[CMFCDesktopAlertWndinfo：m_nURLCmdID](#m_nurlcmdid)命令 ID 的命令将发送给弹出窗口的所有者。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWnd Class](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFC 桌面警报：：创建](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)<br/>
[CMFC 桌面警报对话类](../../mfc/reference/cmfcdesktopalertdialog-class.md)

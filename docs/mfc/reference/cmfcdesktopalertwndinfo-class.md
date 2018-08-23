---
title: CMFCDesktopAlertWndInfo 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_hIcon
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_nURLCmdID
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strText
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strURL
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWndInfo [MFC], m_hIcon
- CMFCDesktopAlertWndInfo [MFC], m_nURLCmdID
- CMFCDesktopAlertWndInfo [MFC], m_strText
- CMFCDesktopAlertWndInfo [MFC], m_strURL
ms.assetid: 5c9bb84e-6c96-4748-8e74-6951b6ae8e84
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d5cf3c8804595aa3d0f3a83bc2628ea830e786a
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540784"
---
# <a name="cmfcdesktopalertwndinfo-class"></a>CMFCDesktopAlertWndInfo 类
`CMFCDesktopAlertWndInfo`类用于[CMFCDesktopAlertWnd 类](../../mfc/reference/cmfcdesktopalertwnd-class.md)。 它指定在桌面警报窗口弹出时显示的控件。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCDesktopAlertWndInfo  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCDesktopAlertWndInfo::operator =](#operator_eq)||  
  
### <a name="data-members"></a>数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon)|句柄显示的图标。|  
|[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)|与在桌面警报窗口上的链接关联的命令 ID。|  
|[CMFCDesktopAlertWndInfo::m_strText](#m_strtext)|在桌面警报窗口显示的文本。|  
|[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)|在桌面警报窗口显示的链接。|  
  
## <a name="remarks"></a>备注  
 `CMFCDesktopAlertWndInfo`类传递给[cmfcdesktopalertwnd:: Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)方法，以指定显示在桌面警报窗口的默认对话框中的元素。 默认对话框可以包含三个项：  
  
-   通过调用设置的图标[CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon)。  
  
-   标签或通过调用设置的短信[CMFCDesktopAlertWndInfo::m_strText](#m_strtext)。  
  
-   链接，通过调用设置[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)。 若要设置时单击该链接时执行的命令，调用[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)。  
  
 如果默认对话框是不够的可以创建一个自定义对话框，并将其传递给[cmfcdesktopalertwnd:: Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)而不是使用此类的方法。 有关详细信息，请参阅[CMFCDesktopAlertDialog 类](../../mfc/reference/cmfcdesktopalertdialog-class.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用中的各种成员`CMFCDesktopAlertWndInfo`类。 该示例演示如何将该句柄设置为显示，则图标显示在桌面警报窗口，在桌面警报窗口中，显示的链接和与在桌面警报窗口上的链接相关联的命令 ID 的文本。 此示例摘自[桌面警报演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxDesktopAlertDialog.h  
  
##  <a name="operator_eq"></a>  CMFCDesktopAlertWndInfo::operator =  
 有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。  
  
```  
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```  
  
### <a name="parameters"></a>参数  
 [in]*src*  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_hicon"></a>  CMFCDesktopAlertWndInfo::m_hIcon  
 句柄显示的图标。  
  
```  
HICON m_hIcon;  
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_nurlcmdid"></a>  CMFCDesktopAlertWndInfo::m_nURLCmdID  
 与在桌面警报窗口上的链接关联的命令 ID。  
  
```  
UINT m_nURLCmdID;  
```  
  
### <a name="remarks"></a>备注  
 当用户单击指定的链接时，命令 ID 发送到的弹出窗口的所有者[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)。  
  
##  <a name="m_strtext"></a>  CMFCDesktopAlertWndInfo::m_strText  
 在桌面警报窗口显示的文本。  
  
```  
CString m_strText;  
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_strurl"></a>  CMFCDesktopAlertWndInfo::m_strURL  
 在桌面警报窗口显示的链接。  
  
```  
CString m_strURL;  
```  
  
### <a name="remarks"></a>备注  
 当用户单击该链接时，该命令，具有[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)命令 ID 将发送到弹出窗口的所有者。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertWnd 类](../../mfc/reference/cmfcdesktopalertwnd-class.md)   
 [Cmfcdesktopalertwnd:: Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)   
 [CMFCDesktopAlertDialog 类](../../mfc/reference/cmfcdesktopalertdialog-class.md)

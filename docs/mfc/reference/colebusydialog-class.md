---
title: "COleBusyDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleBusyDialog
- AFXODLGS/COleBusyDialog
- AFXODLGS/COleBusyDialog::COleBusyDialog
- AFXODLGS/COleBusyDialog::DoModal
- AFXODLGS/COleBusyDialog::GetSelectionType
- AFXODLGS/COleBusyDialog::m_bz
dev_langs:
- C++
helpviewer_keywords:
- Server Not Responding dialog box
- Server Busy dialog box
- COleBusyDialog class
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 0c3ed264cdb83bc97337f13279a20f26b21d454b
ms.lasthandoff: 02/24/2017

---
# <a name="colebusydialog-class"></a>COleBusyDialog 类
用于 OLE“服务器未响应”或“服务器忙”对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class COleBusyDialog : public COleDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|构造 `COleBusyDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleBusyDialog::DoModal](#domodal)|显示 OLE 服务器忙对话框。|  
|[COleBusyDialog::GetSelectionType](#getselectiontype)|确定在该对话框中所做的选择。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[COleBusyDialog::m_bz](#m_bz)|类型的结构**OLEUIBUSY**控制对话框中的行为。|  
  
## <a name="remarks"></a>备注  
 创建类的对象`COleBusyDialog`当你想要调用这些对话框。 之后`COleBusyDialog`构造对象，则可以使用[m_bz](#m_bz)结构初始化的值或在对话框中的控件的状态。 `m_bz`结构属于类型**OLEUIBUSY**。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。  
  
> [!NOTE]
>  应用程序向导生成的容器代码使用此类。  
  
 有关详细信息，请参阅[OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 特定于 OLE 的对话框的详细信息，请参阅文章[OLE 中的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleBusyDialog`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxodlgs.h  
  
##  <a name="colebusydialog"></a>COleBusyDialog::COleBusyDialog  
 此函数只构造`COleBusyDialog`对象。  
  
```  
explicit COleBusyDialog(
    HTASK htaskBusy,  
    BOOL bNotResponding = FALSE,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 *htaskBusy*  
 正在使用中的服务器任务的句柄。  
  
 *bNotResponding*  
 如果**TRUE**，调用而不是服务器忙对话框中的未响应对话框。 未响应对话框中的用语是中服务器忙对话框中的用语略有不同，禁用取消按钮。  
  
 `dwFlags`  
 创建标记。 可以包含零个或多个与按位或运算符结合使用以下值︰  
  
- **BZ_DISABLECANCELBUTTON**时调用对话框中禁用取消按钮。  
  
- **BZ_DISABLESWITCHTOBUTTON**时调用对话框中禁用切换到按钮。  
  
- **BZ_DISABLERETRYBUTTON**时调用对话框中禁用重试按钮。  
  
 `pParentWnd`  
 指向父或所有者窗口对象 (类型的`CWnd`) 对话框对象所属。 如果它是**NULL**，对话框对象的父窗口设置为主应用程序窗口中。  
  
### <a name="remarks"></a>备注  
 若要显示对话框中，调用[DoModal](#domodal)。  
  
 有关详细信息，请参阅[OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="domodal"></a>COleBusyDialog::DoModal  
 调用此函数可显示 OLE 服务器忙或服务器未响应对话框。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 对话框中的完成状态。 以下值之一：  
  
- **IDOK**如果成功显示的对话框。  
  
- **IDCANCEL**如果用户已取消对话框。  
  
- **IDABORT**是否发生了错误。 如果**IDABORT**是返回，调用`COleDialog::GetLastError`成员函数以获取有关发生的错误类型的详细信息。 有关可能出现的错误的列表，请参阅[OleUIBusy](http://msdn.microsoft.com/library/windows/desktop/ms680125) ，此功能在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 如果您想要通过设置成员的初始化各种对话框控件[m_bz](#m_bz)结构中，应执行此操作，然后再调`DoModal`，但在构造对话框对象之后。  
  
 如果`DoModal`返回**IDOK**，可调用其他成员函数来检索的设置或由用户输入的对话框中的信息。  
  
##  <a name="getselectiontype"></a>COleBusyDialog::GetSelectionType  
 调用此函数可获取用户在服务器忙对话框中选择的所选内容类型。  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>返回值  
 所做选择的类型。  
  
### <a name="remarks"></a>备注  
 返回类型值都由指定**选择**枚举类型中声明`COleBusyDialog`类。  
  
```  
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```  
  
 请按照这些值的简短说明︰  
  
- **COleBusyDialog::switchTo**按下了切换到按钮。  
  
- **COleBusyDialog::retry**按下了重试按钮。  
  
- **COleBusyDialog::callUnblocked**调用以激活服务器现在就是未被阻止。  
  
##  <a name="m_bz"></a>COleBusyDialog::m_bz  
 类型的结构**OLEUIBUSY**用来控制服务器忙对话框中的行为。  
  
```  
OLEUIBUSY m_bz;  
```  
  
### <a name="remarks"></a>备注  
 直接或通过成员函数，则可以修改此结构的成员。  
  
 有关详细信息，请参阅[OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [COleDialog 类](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)


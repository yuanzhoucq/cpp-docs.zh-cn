---
title: CDataExchange 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CDataExchange [MFC], CDataExchange
- CDataExchange [MFC], Fail
- CDataExchange [MFC], PrepareCtrl
- CDataExchange [MFC], PrepareEditCtrl
- CDataExchange [MFC], PrepareOleCtrl
- CDataExchange [MFC], m_bSaveAndValidate
- CDataExchange [MFC], m_pDlgWnd
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5972f6224fb7d184e1da29c5251cca8d2f32e276
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337123"
---
# <a name="cdataexchange-class"></a>CDataExchange 类
支持 Microsoft 基础类使用的对话框数据交换 (DDX) 和对话框数据验证 (DDV) 例程。  
  
## <a name="syntax"></a>语法  
  
```  
class CDataExchange  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDataExchange::CDataExchange](#cdataexchange)|构造 `CDataExchange` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDataExchange::Fail](#fail)|当验证失败时调用。 将焦点重置为上一个控件，则引发异常。|  
|[CDataExchange::PrepareCtrl](#preparectrl)|准备用于数据交换或验证指定的控件。 用于 nonedit 控件。|  
|[CDataExchange::PrepareEditCtrl](#prepareeditctrl)|准备用于数据交换或验证指定的编辑控件。|  
|[CDataExchange::PrepareOleCtrl](#prepareolectrl)|准备用于数据交换或验证指定的 OLE 控件。 用于 nonedit 控件。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CDataExchange::m_bSaveAndValidate](#m_bsaveandvalidate)|个方向的 DDX 和 DDV 标志。|  
|[CDataExchange::m_pDlgWnd](#m_pdlgwnd)|其中数据交换的对话框或窗口中会发生。|  
  
## <a name="remarks"></a>备注  
 `CDataExchange` 没有基类。  
  
 使用此类，如果你正在编写数据交换例程的自定义数据类型或控件，或如果你正在编写你自己的数据验证例程。 有关编写自己的 DDX 和 DDV 例程的详细信息，请参阅[技术注意 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)并[对话框](../../mfc/dialog-boxes.md)。  
  
 一个`CDataExchange`对象提供所需的 DDX 和 DDV，才能将放置的上下文信息。 该标志*m_bSaveAndValidate*时 DDX 用于填充数据成员的对话框控件的初始值为 FALSE。 该标志*m_bSaveAndValidate* DDX 用于对话框控件的当前值设置为数据成员和 DDV 用于验证的数据值时为 TRUE。 如果 DDV 验证失败，DDV 过程将显示一个消息框，其中解释了输入的错误。 DDV 过程将调用`Fail`将焦点重置为有问题的控件，并引发异常来停止验证过程。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CDataExchange`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="cdataexchange"></a>  CDataExchange::CDataExchange  
 调用此成员函数来构造`CDataExchange`对象。  
  
```  
CDataExchange(
    CWnd* pDlgWnd,  
    BOOL bSaveAndValidate);
```  
  
### <a name="parameters"></a>参数  
 *pDlgWnd*  
 指向包含该控件的父窗口的指针。 这是通常[CDialog](../../mfc/reference/cdialog-class.md)-派生的对象。  
  
 *bSaveAndValidate*  
 如果为 TRUE，此对象会验证数据，然后将数据从控件写入成员。 如果为 FALSE，此对象将数据从成员到控件。  
  
### <a name="remarks"></a>备注  
 构造`CDataExchange`对象自己来存储数据 exchange 对象传递给您的窗口中的额外信息[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]  
  
##  <a name="fail"></a>  CDataExchange::Fail  
 对话框数据验证 (DDV) 操作失败时，框架将调用此成员函数。  
  
```  
void Fail();
```  
  
### <a name="remarks"></a>备注  
 `Fail` 将焦点和选择内容还原到其验证失败 （如果要还原的控件） 的控件。 `Fail` 然后将引发异常的类型[CUserException](../../mfc/reference/cuserexception-class.md)停止验证过程。 该异常会导致解释了该错误将显示一个消息框。 DDV 验证失败后，用户可以重新输入有问题的控件中的数据。  
  
 自定义 DDV 例程的实现者可以调用`Fail`从其例程在验证失败时。  
  
 有关编写自己的 DDX 和 DDV 例程的详细信息，请参阅[技术注意 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)并[对话框主题](../../mfc/dialog-boxes.md)。  
  
##  <a name="m_bsaveandvalidate"></a>  CDataExchange::m_bSaveAndValidate  
 此标志指示对话框数据交换 (DDX) 操作的方向。  
  
```  
BOOL m_bSaveAndValidate;  
```  
  
### <a name="remarks"></a>备注  
 为非零值标志如果`CDataExchange`对象用于将数据从对话框控件到对话框类数据成员后用户编辑控件。 如果该对象用于初始化的对话框类数据成员的对话框控件，该标志为零。  
  
 对话框数据验证 (DDV) 期间还是非零值标志。  
  
 有关编写自己的 DDX 和 DDV 例程的详细信息，请参阅[技术注意 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)并[对话框主题](../../mfc/dialog-boxes.md)。  
  
##  <a name="m_pdlgwnd"></a>  CDataExchange::m_pDlgWnd  
 包含一个指向[CWnd](../../mfc/reference/cwnd-class.md)的对话框数据交换 (DDX) 或验证 (DDV) 所需位置的对象。  
  
```  
CWnd* m_pDlgWnd;  
```  
  
### <a name="remarks"></a>备注  
 此对象通常是[CDialog](../../mfc/reference/cdialog-class.md)对象。 自定义的 DDX 或 DDV 例程的实现器可以使用此指针以获取对包含的控件正在其的对话框窗口的访问权限。  
  
 有关编写自己的 DDX 和 DDV 例程的详细信息，请参阅[技术注意 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)并[对话框主题](../../mfc/dialog-boxes.md)。  
  
##  <a name="preparectrl"></a>  CDataExchange::PrepareCtrl  
 框架调用此成员函数以准备对话框数据交换 (DDX) 和验证 (DDV) 指定的控件。  
  
```  
HWND PrepareCtrl(int nIDC);
```  
  
### <a name="parameters"></a>参数  
 *nIDC*  
 要针对 DDX 或 DDV 准备该控件的 ID。  
  
### <a name="return-value"></a>返回值  
 正在准备好 DDX 或 DDV 该控件的 HWND。  
  
### <a name="remarks"></a>备注  
 使用[PrepareEditCtrl](#prepareeditctrl)改为编辑控件; 对于所有其他控件使用此成员函数。  
  
 存储中的控件的 HWND 包含准备`CDataExchange`类。 框架使用此句柄将焦点还原到以前具有焦点的控件的 DDX 或 DDV 故障发生。  
  
 自定义的 DDX 或 DDV 例程的实现器应调用`PrepareCtrl`它们是交换数据通过 DDX 或验证通过 DDV 数据的所有非编辑控件。  
  
 有关编写自己的 DDX 和 DDV 例程的详细信息，请参阅[技术注意 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)并[对话框主题](../../mfc/dialog-boxes.md)。  
  
##  <a name="prepareeditctrl"></a>  CDataExchange::PrepareEditCtrl  
 框架调用此成员函数以准备指定的编辑控件的对话框数据交换 (DDX) 和验证 (DDV)。  
  
```  
HWND PrepareEditCtrl(int nIDC);
```  
  
### <a name="parameters"></a>参数  
 *nIDC*  
 准备用于 DDX 或 DDV 编辑控件的 ID。  
  
### <a name="return-value"></a>返回值  
 正在准备好 DDX 或 DDV 在编辑控件的 HWND。  
  
### <a name="remarks"></a>备注  
 使用[PrepareCtrl](#preparectrl)改为所有非编辑控件。  
  
 准备包含以下两项。 首先，`PrepareEditCtrl`存储中的控件的 HWND`CDataExchange`类。 框架使用此句柄将焦点还原到以前具有焦点的控件的 DDX 或 DDV 故障发生。 第二个，`PrepareEditCtrl`中设置一个标志`CDataExchange`类，以指示其数据交换或验证是一个编辑控件的控件。  
  
 自定义的 DDX 或 DDV 例程的实现器应调用`PrepareEditCtrl`的所有编辑的控件，它们是交换数据通过 DDX 或验证通过 DDV 数据。  
  
 有关编写自己的 DDX 和 DDV 例程的详细信息，请参阅[技术注意 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)并[对话框主题](../../mfc/dialog-boxes.md)。  
  
##  <a name="prepareolectrl"></a>  CDataExchange::PrepareOleCtrl  
 框架调用此成员函数以准备对话框数据交换 (DDX) 和验证 (DDV) 指定的 OLE 控件。  
  
```  
COleControlSite* PrepareOleCtrl(int nIDC);
```  
  
### <a name="parameters"></a>参数  
 *nIDC*  
 准备用于 DDX 或 DDV OLE 控件的 ID。  
  
### <a name="return-value"></a>返回值  
 指向 OLE 控件所在位置的指针。  
  
### <a name="remarks"></a>备注  
 使用[PrepareEditCtrl](#prepareeditctrl)改为编辑控件或[PrepareCtrl](#preparectrl)所有其他非 OLE 控件的。  
  
 自定义的 DDX 或 DDV 例程的实现器应调用`PrepareOleCtrl`它们是交换数据通过 DDX 或验证通过 DDV 数据的所有 OLE 控件的。  
  
 有关编写自己的 DDX 和 DDV 例程的详细信息，请参阅[技术注意 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)并[对话框主题](../../mfc/dialog-boxes.md)。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 VIEWEX](../../visual-cpp-samples.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)   
 [CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)


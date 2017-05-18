---
title: "CDataExchange 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- DDX/DDV, Technical Note 26
- DDX/DDV, CDataExchange class
- DDX (dialog data exchange), direction of exchange
- DDX (dialog data exchange), between dialog and CDialog
- DDX (dialog data exchange), custom DDX routines
- DDV (dialog data validation)
- m_bSaveAndValidate
- CDataExchange class
- exchanging data between dialogs and CDialogs
- DDV (dialog data validation), custom DDV routines
- DDX/DDV
- DDX (dialog data exchange)
- validating data, dialog box data entry
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 8f35e87d562a894411401755ccd4fdd54e43b58a
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

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
|[CDataExchange::CDataExchange](#cdataexchange)|构造 `CDataExchange` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDataExchange::Fail](#fail)|当验证失败时调用。 将焦点重置为上一个控件，并引发异常。|  
|[CDataExchange::PrepareCtrl](#preparectrl)|准备以进行数据交换或验证指定的控件。 用于 nonedit 控件。|  
|[CDataExchange::PrepareEditCtrl](#prepareeditctrl)|准备以进行数据交换或验证指定的编辑控件。|  
|[CDataExchange::PrepareOleCtrl](#prepareolectrl)|准备以进行数据交换或验证指定的 OLE 控件。 用于 nonedit 控件。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CDataExchange::m_bSaveAndValidate](#m_bsaveandvalidate)|用于表示的 DDX 和 DDV 方向标志。|  
|[CDataExchange::m_pDlgWnd](#m_pdlgwnd)|数据交换在对话框中的一个或多个窗口中会发生。|  
  
## <a name="remarks"></a>备注  
 `CDataExchange`没有基类的类。  
  
 使用此类，如果您正在编写数据交换例程的自定义数据类型或控件，或如果您正在编写您自己的数据验证例程。 编写您自己的 DDX 和 DDV 例程的详细信息，请参阅[技术注意 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)和[对话框](../../mfc/dialog-boxes.md)。  
  
 一个`CDataExchange`对象提供所需的 DDX 和 DDV，才能将放置的上下文信息。 该标志`m_bSaveAndValidate`是**FALSE** DDX 用于填充数据成员的对话框控件的初始值。 该标志`m_bSaveAndValidate`是**TRUE**当 DDX 用于对话框控件的当前值设置为数据成员和 DDV 用于验证数据值。 如果 DDV 验证失败，DDV 过程将显示一个消息框，解释了该输入的错误。 DDV 过程将调用**失败**将焦点重置为有问题的控件，并引发异常来停止验证过程。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CDataExchange`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="cdataexchange"></a>CDataExchange::CDataExchange  
 调用此成员函数来构造`CDataExchange`对象。  
  
```  
CDataExchange(
    CWnd* pDlgWnd,  
    BOOL bSaveAndValidate);
```  
  
### <a name="parameters"></a>参数  
 *pDlgWnd*  
 指向包含该控件的父窗口的指针。 通常，这是[CDialog](../../mfc/reference/cdialog-class.md)-派生的对象。  
  
 `bSaveAndValidate`  
 如果**TRUE**，此对象会验证数据，然后将数据从控件写入到的成员。 如果**FALSE**，此对象将数据从成员到控件。  
  
### <a name="remarks"></a>备注  
 构造`CDataExchange`对象自己来存储数据 exchange 对象传递给您的窗口中的额外信息[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog #&70;](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]  
  
##  <a name="fail"></a>CDataExchange::Fail  
 对话框数据验证 (DDV) 操作失败时，框架将调用此成员函数。  
  
```  
void Fail();
```  
  
### <a name="remarks"></a>备注  
 **失败**将焦点和选择内容还原为其验证失败 （如果要还原的控件） 的控件。 **失败**然后引发异常的类型[CUserException](../../mfc/reference/cuserexception-class.md)停止验证过程。 该异常将导致解释了该错误将会显示一个消息框。 DDV 验证操作失败后，用户可以重新输入有问题的控件中的数据。  
  
 自定义 DDV 例程的实现器可以调用**失败**从验证失败时其例程。  
  
 编写您自己的 DDX 和 DDV 例程的详细信息，请参阅[技术注意 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)和[对话框主题](../../mfc/dialog-boxes.md)。  
  
##  <a name="m_bsaveandvalidate"></a>CDataExchange::m_bSaveAndValidate  
 此标志指示的对话框数据交换 (DDX) 操作的方向。  
  
```  
BOOL m_bSaveAndValidate;  
```  
  
### <a name="remarks"></a>备注  
 标记为非零值如果`CDataExchange`对象用于将数据从移动对话框控件到对话框类数据成员之后用户编辑控件。 如果该对象用于初始化对话框类数据成员的对话框控件，该标志为零。  
  
 该标志期间对话框数据验证 (DDV) 还是非零值。  
  
 编写您自己的 DDX 和 DDV 例程的详细信息，请参阅[技术注意 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)和[对话框主题](../../mfc/dialog-boxes.md)。  
  
##  <a name="m_pdlgwnd"></a>CDataExchange::m_pDlgWnd  
 包含一个指向[CWnd](../../mfc/reference/cwnd-class.md)对象的对话框数据交换 (DDX) 或验证 (DDV) 发生的情况。  
  
```  
CWnd* m_pDlgWnd;  
```  
  
### <a name="remarks"></a>备注  
 此对象通常是[CDialog](../../mfc/reference/cdialog-class.md)对象。 自定义的 DDX 或 DDV 例程的实现器可以使用此指针以获取对包含的控件正在其的对话框窗口的访问权限。  
  
 编写您自己的 DDX 和 DDV 例程的详细信息，请参阅[技术注意 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)和[对话框主题](../../mfc/dialog-boxes.md)。  
  
##  <a name="preparectrl"></a>CDataExchange::PrepareCtrl  
 框架调用此成员函数以准备对话框数据交换 (DDX) 和验证 (DDV) 指定的控件。  
  
```  
HWND PrepareCtrl(int nIDC);
```  
  
### <a name="parameters"></a>参数  
 `nIDC`  
 要准备用于 DDX 或 DDV 控件的 ID。  
  
### <a name="return-value"></a>返回值  
 `HWND` DDX 或 DDV 正准备的控件。  
  
### <a name="remarks"></a>备注  
 使用[PrepareEditCtrl](#prepareeditctrl)改为编辑控件; 对于所有其他控件使用此成员函数。  
  
 存储控件的包含准备`HWND`中`CDataExchange`类。 框架将使用此句柄将焦点还原到的 DDX 或 DDV 故障发生之前具有焦点的控件。  
  
 自定义的 DDX 或 DDV 例程的实现器应调用`PrepareCtrl`它们被交换数据通过 DDX 或验证通过 DDV 数据的所有非编辑控件。  
  
 编写您自己的 DDX 和 DDV 例程的详细信息，请参阅[技术注意 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)和[对话框主题](../../mfc/dialog-boxes.md)。  
  
##  <a name="prepareeditctrl"></a>CDataExchange::PrepareEditCtrl  
 框架调用此成员函数以准备对话框数据交换 (DDX) 和验证 (DDV) 指定的编辑控件。  
  
```  
HWND PrepareEditCtrl(int nIDC);
```  
  
### <a name="parameters"></a>参数  
 `nIDC`  
 要准备用于 DDX 或 DDV 编辑控件的 ID。  
  
### <a name="return-value"></a>返回值  
 `HWND`正准备的 DDX 或 DDV 编辑控件。  
  
### <a name="remarks"></a>备注  
 使用[PrepareCtrl](#preparectrl)改为所有非编辑控件。  
  
 准备由以下两个操作组成。 首先，`PrepareEditCtrl`存储控件的`HWND`中`CDataExchange`类。 框架将使用此句柄将焦点还原到的 DDX 或 DDV 故障发生之前具有焦点的控件。 第二个，`PrepareEditCtrl`中设置一个标志`CDataExchange`类，以指示其数据交换或验证是编辑控件的控件。  
  
 自定义的 DDX 或 DDV 例程的实现器应调用`PrepareEditCtrl`的所有编辑的控件，它们被交换数据通过 DDX 或验证通过 DDV 数据。  
  
 编写您自己的 DDX 和 DDV 例程的详细信息，请参阅[技术注意 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)和[对话框主题](../../mfc/dialog-boxes.md)。  
  
##  <a name="prepareolectrl"></a>CDataExchange::PrepareOleCtrl  
 框架调用此成员函数以指定的 OLE 控件准备对话框数据交换 (DDX) 和验证 (DDV)。  
  
```  
COleControlSite* PrepareOleCtrl(int nIDC);
```  
  
### <a name="parameters"></a>参数  
 `nIDC`  
 要准备用于 DDX 或 DDV OLE 控件的 ID。  
  
### <a name="return-value"></a>返回值  
 指向 OLE 控件所在位置的指针。  
  
### <a name="remarks"></a>备注  
 使用[PrepareEditCtrl](#prepareeditctrl)改为编辑控件或[PrepareCtrl](#preparectrl)对于所有其他非 OLE 控件。  
  
 自定义的 DDX 或 DDV 例程的实现器应调用`PrepareOleCtrl`它们被交换数据通过 DDX 或验证通过 DDV 数据的所有 OLE 控件的。  
  
 编写您自己的 DDX 和 DDV 例程的详细信息，请参阅[技术注意 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有关 DDX 和 DDV 的概述，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)和[对话框主题](../../mfc/dialog-boxes.md)。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 VIEWEX](../../visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)   
 [CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)



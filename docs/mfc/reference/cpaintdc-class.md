---
title: CPaintDC 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPaintDC
- AFXWIN/CPaintDC
- AFXWIN/CPaintDC::CPaintDC
- AFXWIN/CPaintDC::m_ps
- AFXWIN/CPaintDC::m_hWnd
dev_langs:
- C++
helpviewer_keywords:
- CPaintDC [MFC], CPaintDC
- CPaintDC [MFC], m_ps
- CPaintDC [MFC], m_hWnd
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d9f83c36a9c1a0d334e3b4a75724521d5711123e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376530"
---
# <a name="cpaintdc-class"></a>CPaintDC 类
设备上下文类派生自[CDC](../../mfc/reference/cdc-class.md)。  
  
## <a name="syntax"></a>语法  
  
```  
class CPaintDC : public CDC  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CPaintDC::CPaintDC](#cpaintdc)|构造`CPaintDC`连接到指定[CWnd](../../mfc/reference/cwnd-class.md)。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CPaintDC::m_ps](#m_ps)|包含[PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md)用于绘制的工作区。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CPaintDC::m_hWnd](#m_hwnd)|`HWND`此`CPaintDC`附加对象。|  
  
## <a name="remarks"></a>备注  
 它执行[cwnd:: Beginpaint](../../mfc/reference/cwnd-class.md#beginpaint)在构造时和[CWnd::EndPaint](../../mfc/reference/cwnd-class.md#endpaint)在析构时。  
  
 A`CPaintDC`对象仅可在时响应[WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213)消息时，通常在你`OnPaint`消息处理程序成员函数。  
  
 有关详细信息使用`CPaintDC`，请参阅[设备上下文](../../mfc/device-contexts.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CPaintDC`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="cpaintdc"></a>  CPaintDC::CPaintDC  
 构造`CPaintDC`对象，为绘制，准备应用程序窗口，并将存储[PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md)结构[m_ps](#m_ps)成员变量。  
  
```  
explicit CPaintDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向`CWnd`对象`CPaintDC`对象所属。  
  
### <a name="remarks"></a>备注  
 异常 (类型的`CResourceException`) 如果则会引发 Windows [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871)调用将失败。 设备上下文可能不可用，如果 Windows 已分配所有可用的设备上下文。 你的应用程序竞争可用在任何给定时间在 Windows 下的五个常见显示上下文。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>  CPaintDC::m_hWnd  
 `HWND`此`CPaintDC`附加对象。  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>备注  
 `m_hWnd` 是一个受保护的类型变量`HWND`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]  
  
##  <a name="m_ps"></a>  CPaintDC::m_ps  
 `m_ps` 是类型的公共成员变量[PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md)。  
  
```  
PAINTSTRUCT m_ps;  
```  
  
### <a name="remarks"></a>备注  
 它是`PAINTSTRUCT`是传递给，可以通过填写[cwnd:: Beginpaint](../../mfc/reference/cwnd-class.md#beginpaint)。  
  
 `PAINTSTRUCT`包含应用程序使用绘制与关联的窗口的客户端区域的信息`CPaintDC`对象。  
  
 请注意，你可以访问的设备上下文句柄通过`PAINTSTRUCT`。 但是，你可以访问的句柄更直接通过`m_hDC`成员变量，`CPaintDC`继承自`CDC`。  
  
### <a name="example"></a>示例  
  请参阅示例[CPaintDC::m_hWnd](#m_hwnd)。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 MDI](../../visual-cpp-samples.md)   
 [CDC 类](../../mfc/reference/cdc-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)




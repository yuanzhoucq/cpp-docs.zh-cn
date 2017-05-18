---
title: "CWindowDC 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWindowDC
- No header/CWindowDC
- No header/CWindowDC::CWindowDC
- No header/CWindowDC::m_hWnd
dev_langs:
- C++
helpviewer_keywords:
- device contexts, window
- screen output classes
- CWindowDC class
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 8a941e1b6f8a398706498ec5d1ce1bfc9156f115
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cwindowdc-class"></a>CWindowDC 类
从 `CDC`派生。  
  
## <a name="syntax"></a>语法  
  
```  
class CWindowDC : public CDC  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CWindowDC::CWindowDC](#cwindowdc)|构造 `CWindowDC` 对象。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CWindowDC::m_hWnd](#m_hwnd)|`HWND`此`CWindowDC`附加。|  
  
## <a name="remarks"></a>备注  
 调用 Windows 函数[GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947\(v=vs.85\).aspx)在构造时和[ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920\(v=vs.85\).aspx)在析构时。 这意味着，`CWindowDC`对象访问的整个屏幕区域[CWnd](../../mfc/reference/cwnd-class.md) （客户端和非工作区）。  
  
 有关详细信息使用`CWindowDC`，请参阅[设备上下文](../../mfc/device-contexts.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CWindowDC`  
  
## <a name="requirements"></a>要求  
 标头︰ afxwin.h  
  
##  <a name="cwindowdc"></a>CWindowDC::CWindowDC  
 构造`CWindowDC`访问的整个屏幕区域 （客户端和非工作区） 的对象`CWnd`指向对象`pWnd`。  
  
```  
explicit CWindowDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 访问的设备上下文对象将其工作区窗口中。  
  
### <a name="remarks"></a>备注  
 构造函数调用 Windows 函数[GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947)。  
  
 异常 (类型的`CResourceException`) 如果则会引发 Windows`GetWindowDC`调用将失败。 设备上下文可能不可用，如果 Windows 已分配所有可用的设备上下文。 您的应用程序都可用在 Windows 下任何给定时间的五个常见显示上下文争用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&188;](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>CWindowDC::m_hWnd  
 `HWND`的`CWnd`指针用于构造`CWindowDC`对象。  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>备注  
 `m_hWnd`是一个受保护的类型变量`HWND`。  
  
### <a name="example"></a>示例  
  请参阅示例[CWindowDC::CWindowDC](#cwindowdc)。  
  
## <a name="see-also"></a>另请参阅  
 [CDC 类](../../mfc/reference/cdc-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDC 类](../../mfc/reference/cdc-class.md)


---
title: CDockState 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDockState
- AFXADV/CDockState
- AFXADV/CDockState::Clear
- AFXADV/CDockState::GetVersion
- AFXADV/CDockState::LoadState
- AFXADV/CDockState::SaveState
- AFXADV/CDockState::m_arrBarInfo
dev_langs:
- C++
helpviewer_keywords:
- CDockState [MFC], Clear
- CDockState [MFC], GetVersion
- CDockState [MFC], LoadState
- CDockState [MFC], SaveState
- CDockState [MFC], m_arrBarInfo
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fcfbe14743ffff91a4a1749f0394a6deb8f0547a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367433"
---
# <a name="cdockstate-class"></a>CDockState 类
在永久性内存（文件）中加载、卸载或清除一个或多个停靠控件条状态的序列化 `CObject` 类。  
  
## <a name="syntax"></a>语法  
  
```  
class CDockState : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDockState::Clear](#clear)|清除停靠状态信息。|  
|[CDockState::GetVersion](#getversion)|检索存储的版本号栏状态。|  
|[CDockState::LoadState](#loadstate)|检索状态信息从注册表或。INI 文件。|  
|[CDockState::SaveState](#savestate)|将状态信息保存到注册表或 INI 文件。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|指向存储的指针的数组将停靠包含与每个控件条的一个项的状态信息。|  
  
## <a name="remarks"></a>备注  
 停靠状态包括大小和位置的栏和停靠。 当检索存储停靠状态，`CDockState`检查栏的位置和如果栏不可见使用当前的屏幕设置，`CDockState`缩放条的位置以使其可见。 主要用途`CDockState`是保持大量的控件条的整个状态并允许该状态保存和加载到注册表中，应用程序的。INI 文件，或以二进制形式的一部分`CArchive`对象的内容。  
  
 栏可以是任何可停靠控件条，包括工具栏、 状态栏或对话栏。 `CDockState` 编写并读取到或从通过文件对象`CArchive`对象。  
  
 [CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate)检索的框架窗口的状态信息`CControlBar`对象，并将其放`CDockState`对象。 然后，便可以编写的内容`CDockState`对象到存储，同时[序列化](../../mfc/reference/cobject-class.md#serialize)或[CDockState::SaveState](#savestate)。 如果你以后想要还原的框架窗口中的控件栏状态，则可以加载将状态与`Serialize`或[CDockState::LoadState](#loadstate)，然后使用[CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate)应用保存状态设置为框架窗口的控件条。  
  
 停靠控件条的详细信息，请参阅文章[控件条](../../mfc/control-bars.md)，[工具栏： 停靠和浮动](../../mfc/docking-and-floating-toolbars.md)，和[框架窗口](../../mfc/frame-windows.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDockState`  
  
## <a name="requirements"></a>要求  
 **标头：** afxadv.h  
  
##  <a name="clear"></a>  CDockState::Clear  
 调用此函数可清除所有停靠的信息存储在`CDockState`对象。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>备注  
 这包括不仅是否栏固定，但条形图的大小和位置以及可见。  
  
##  <a name="getversion"></a>  CDockState::GetVersion  
 调用此函数可检索存储的版本号栏状态。  
  
```  
DWORD GetVersion();
```  
  
### <a name="return-value"></a>返回值  
 如果存储的栏信息是早于当前栏状态;2 如果存储的栏信息等同于当前栏状态。  
  
### <a name="remarks"></a>备注  
 版本支持修改后的栏，以添加新的持久性属性和仍将能够检测并加载由栏的早期版本创建的持久性状态。  
  
##  <a name="loadstate"></a>  CDockState::LoadState  
 调用此函数可从注册表检索状态信息或。INI 文件。  
  
```  
void LoadState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>参数  
 `lpszProfileName`  
 指向以 null teminated 字符串，初始化文件或 Windows 注册表状态信息的存储位置中的键中指定的节名称。  
  
### <a name="remarks"></a>备注  
 配置文件名称是在应用程序的部分。INI 文件或注册表中包含的栏的状态信息。 你可以将控制条状态信息保存到注册表或。INI 文件`SaveState`。  
  
##  <a name="m_arrbarinfo"></a>  CDockState::m_arrBarInfo  
 A`CPtrArray`是指向已保存状态信息在每个控件条的存储的控制栏信息的指针的数组的对象`CDockState`对象。  
  
```  
CPtrArray m_arrBarInfo;  
```  
  
##  <a name="savestate"></a>  CDockState::SaveState  
 调用此函数可将状态信息保存到注册表或。INI 文件。  
  
```  
void SaveState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>参数  
 `lpszProfileName`  
 指向以 null teminated 字符串，初始化文件或 Windows 注册表状态信息的存储位置中的键中指定的节名称。  
  
### <a name="remarks"></a>备注  
 配置文件名称是在应用程序的部分。INI 文件或注册表，其中包含控件条的状态信息。 `SaveState` 此外将保存当前屏幕的大小。 你可以从注册表检索控件栏信息或。INI 文件`LoadState`。  
  
## <a name="see-also"></a>请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)


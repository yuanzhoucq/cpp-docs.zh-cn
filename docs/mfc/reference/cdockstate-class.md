---
title: "CDockState 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- dock state
- size
- docking control bars
- CDockState class
- states, dockable control bar
- position, control bar
- size, control bar
- docking tool windows
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
caps.latest.revision: 23
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
ms.openlocfilehash: fc8beb80cc35c1816fbc305ece2bfbc5df2e7cd0
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cdockstate-class"></a>CDockState 类
在永久性内存（文件）中加载、卸载或清除一个或多个停靠控件条状态的序列化 `CObject` 类。  
  
## <a name="syntax"></a>语法  
  
```  
class CDockState : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CDockState::Clear](#clear)|清除停靠状态信息。|  
|[CDockState::GetVersion](#getversion)|检索存储的版本编号栏状态。|  
|[CDockState::LoadState](#loadstate)|检索状态信息从注册表或。INI 文件中。|  
|[CDockState::SaveState](#savestate)|将状态信息保存到注册表或 INI 文件中。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|指向存储的指针数组停靠包含与每个控件条的一个项的状态信息。|  
  
## <a name="remarks"></a>备注  
 停靠状态包括大小和位置的栏和停靠。 当检索存储停靠状态，`CDockState`检查条形图的位置和栏不可见的当前屏幕设置，`CDockState`缩放栏的放置，以使它是可见的。 主要用途`CDockState`是以容纳大量的控件条的整个状态，并允许该状态保存并加载到注册表中，应用程序的。INI 文件或以二进制形式的一部分`CArchive`对象的内容。  
  
 栏可以是任何可停靠栏，其中包括工具栏、 状态栏、 或对话栏控件。 `CDockState`写入和读取，或者通过文件中读取对象`CArchive`对象。  
  
 [CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate)检索的框架窗口的状态信息`CControlBar`对象，并将其放`CDockState`对象。 然后可以编写的内容`CDockState`对象传递给存储与使用[Serialize](../../mfc/reference/cobject-class.md#serialize)或[CDockState::SaveState](#savestate)。 如果您以后想要还原的控制条在框架窗口中的状态，则可以加载将状态与`Serialize`或[CDockState::LoadState](#loadstate)，然后使用[CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate)要应用于框架窗口的控件条的已保存的状态。  
  
 停靠控件条的详细信息，请参阅文章[控件条](../../mfc/control-bars.md)，[工具栏︰ 停靠和浮动](../../mfc/docking-and-floating-toolbars.md)，和[框架窗口](../../mfc/frame-windows.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDockState`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxadv.h  
  
##  <a name="clear"></a>CDockState::Clear  
 调用此函数可清除所有停靠的信息存储在`CDockState`对象。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>备注  
 这包括不仅是否栏固定与否，但条形图的大小和位置，无论是否均可见。  
  
##  <a name="getversion"></a>CDockState::GetVersion  
 调用此函数可检索存储的版本编号栏状态。  
  
```  
DWORD GetVersion();
```  
  
### <a name="return-value"></a>返回值  
 1 如果存储栏的信息是早于当前状态，则栏2 if 存储的栏信息等同于当前栏状态。  
  
### <a name="remarks"></a>备注  
 版本支持，可修改后的栏，以添加新的持久性属性，仍将能够检测和加载由栏的早期版本创建的持久性状态。  
  
##  <a name="loadstate"></a>CDockState::LoadState  
 调用此函数可从注册表中检索状态信息或。INI 文件中。  
  
```  
void LoadState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>参数  
 `lpszProfileName`  
 指向以 null teminated 字符串，初始化文件或注册表项的 Windows 状态信息都存储在指定的节名称。  
  
### <a name="remarks"></a>备注  
 配置文件名称是在应用程序的部分。INI 文件或注册表中包含的条的状态信息。 可以将控制条状态信息保存到注册表或。INI 文件`SaveState`。  
  
##  <a name="m_arrbarinfo"></a>CDockState::m_arrBarInfo  
 一个`CPtrArray`对象，它是指向已保存状态信息在每个控件条的存储的控制条信息的指针的数组`CDockState`对象。  
  
```  
CPtrArray m_arrBarInfo;  
```  
  
##  <a name="savestate"></a>CDockState::SaveState  
 调用此函数可将状态信息保存到注册表或。INI 文件中。  
  
```  
void SaveState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>参数  
 `lpszProfileName`  
 指向以 null teminated 字符串，初始化文件或注册表项的 Windows 状态信息都存储在指定的节名称。  
  
### <a name="remarks"></a>备注  
 配置文件名称是在应用程序的部分。INI 文件或注册表，其中包含控件条状态信息。 `SaveState`此外将保存当前的屏幕尺寸。 您可以从注册表检索控件栏信息或。INI 文件`LoadState`。  
  
## <a name="see-also"></a>另请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)



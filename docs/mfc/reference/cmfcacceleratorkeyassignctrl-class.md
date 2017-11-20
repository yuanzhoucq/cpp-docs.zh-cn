---
title: "CMFCAcceleratorKeyAssignCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::GetAccel
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsFocused
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsKeyDefined
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::ResetKey
dev_langs: C++
helpviewer_keywords:
- CMFCAcceleratorKeyAssignCtrl [MFC], CMFCAcceleratorKeyAssignCtrl
- CMFCAcceleratorKeyAssignCtrl [MFC], GetAccel
- CMFCAcceleratorKeyAssignCtrl [MFC], IsFocused
- CMFCAcceleratorKeyAssignCtrl [MFC], IsKeyDefined
- CMFCAcceleratorKeyAssignCtrl [MFC], PreTranslateMessage
- CMFCAcceleratorKeyAssignCtrl [MFC], ResetKey
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
caps.latest.revision: "33"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6b135937adfe9b1e30747c35883692be54ba77e4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>CMFCAcceleratorKeyAssignCtrl 类
`CMFCAcceleratorKeyAssignCtrl`类扩展[CEdit 类](../../mfc/reference/cedit-class.md)以支持额外的系统按钮，如 ALT、 CONTROL 和 SHIFT。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCAcceleratorKeyAssignCtrl : public CEdit  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|构造 `CMFCAcceleratorKeyAssignCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|检索 `CMFCAcceleratorKeyAssignCtrl` 对象中按下的快捷键的 `ACCEL` 结构。|  
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||  
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|确定是否已定义快捷键。|  
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|在将窗口消息发送到 [TranslateMessage](../../mfc/reference/cwinapp-class.md) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) Windows 函数之前，由 [CWinApp](http://msdn.microsoft.com/library/windows/desktop/ms644934) 类用于对此消息进行转换。 （重写 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。）|  
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|重置快捷键。|  
  
## <a name="remarks"></a>备注  
 此类通过支持快捷键（也称为加速键）来扩展 `CEdit` 类的功能。 `CMFCAcceleratorKeyAssignCtrl`类用作[CEdit 类](../../mfc/reference/cedit-class.md)和它还能识别系统按钮。  
  
 此类会将物理快捷键组合映射到字符串值。 例如，假定键组合 ALT + B 映射到字符串“Alt + B”。 当用户按下 `CMFCAcceleratorKeyAssignCtrl` 对象中的此键组合时，会向用户显示“Alt + B”。 有关快捷键和字符串格式之间的映射的详细信息，请参阅[CMFCAcceleratorKey 类](../../mfc/reference/cmfcacceleratorkey-class.md)。  
  
## <a name="example"></a>示例  
 下列示例演示如何构造 `CMFCAcceleratorKeyAssignCtrl` 对象并使用其 `ResetKey` 方法来重置快捷键。  
  
 [!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 `CMFCAcceleratorKeyAssignCtrl`   
  
## <a name="requirements"></a>要求  
 **标头：** afxacceleratorkeyassignctrl.h  
  
##  <a name="cmfcacceleratorkeyassignctrl"></a>CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl  
 构造[CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)对象。  
  
```  
CMFCAcceleratorKeyAssignCtrl();
```  
  
##  <a name="getaccel"></a>CMFCAcceleratorKeyAssignCtrl::GetAccel  
 检索`ACCEL`结构中的按下的快捷键[CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)对象。  
  
```  
ACCEL const* GetAccel() const;  
```  
  
### <a name="return-value"></a>返回值  
 `ACCEL`描述的快捷键的结构。  
  
### <a name="remarks"></a>备注  
 使用此函数可检索`ACCEL`用户输入到的快捷键的结构你`CMFCAcceleratorKeyAssignCtrl`对象。  
  
##  <a name="isfocused"></a>CMFCAcceleratorKeyAssignCtrl::IsFocused  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsFocused() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="iskeydefined"></a>CMFCAcceleratorKeyAssignCtrl::IsKeyDefined  
 确定是否已在定义的快捷键[CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)对象。  
  
```  
BOOL IsKeyDefined() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果用户具有已按定义的快捷键; 的密钥的有效组合否则为 0。  
  
### <a name="remarks"></a>备注  
 使用此函数可确定用户是否输入中的有效快捷键你`CMFCAcceleratorKeyAssignCtrl`对象。 如果存在的快捷键，则可以使用[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)方法来获取`ACCEL`结构与此快捷键相关联。  
  
##  <a name="pretranslatemessage"></a>CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>参数  
 [in] `pMsg`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="resetkey"></a>CMFCAcceleratorKeyAssignCtrl::ResetKey  
 重置快捷键。  
  
```  
void ResetKey();
```  
  
### <a name="remarks"></a>备注  
 该函数将清除编辑控件文本。 这包括用户按下任何快捷键。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCAcceleratorKey 类](../../mfc/reference/cmfcacceleratorkey-class.md)

---
title: "CMFCAcceleratorKey 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
dev_langs:
- C++
helpviewer_keywords:
- CMFCAcceleratorKey class
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
caps.latest.revision: 36
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
ms.openlocfilehash: 7baa210acfabe8f17e2ab747fd98fe463c2907a2
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcacceleratorkey-class"></a>CMFCAcceleratorKey 类
实现虚拟键映射和格式设置的帮助器类。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCAcceleratorKey : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|构造 `CMFCAcceleratorKey` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCAcceleratorKey::Format](#format)|将转换为它的可视表示形式的加速结构。|  
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|设置的快捷键`CMFCAcceleratorKey`对象。|  
  
## <a name="remarks"></a>备注  
 快捷键也被称为键盘快捷方式。 如果您想要显示键盘快捷方式的用户输入时， [CMFCAcceleratorKeyAssignCtrl 类](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)映射键盘快捷方式，如 Alt + Shift + S，为自定义文本的格式，如"Alt + Shift + S"。 每个`CMFCAcceleratorKey`对象映射到文本格式的单个快捷键。  
  
 有关如何使用键盘快捷方式和快捷键对应表的详细信息，请参阅[CKeyboardManager 类](../../mfc/reference/ckeyboardmanager-class.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何构造`CMFCAcceleratorKey`对象以及如何使用其`Format`方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&30;](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCAcceleratorKey`   
  
## <a name="requirements"></a>要求  
 **标头︰** afxacceleratorkey.h  
  
##  <a name="cmfcacceleratorkey"></a>CMFCAcceleratorKey::CMFCAcceleratorKey  
 构造[CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)对象。  
  
```  
CMFCAcceleratorKey();  
CMFCAcceleratorKey(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpAccel`  
 快捷方式键指向的指针。  
  
### <a name="remarks"></a>备注  
 如果你未提供的快捷键在创建时`CMFCAccleratorKey`，使用[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)方法将与快捷键关联起来您`CMFCAcceleratorKey`对象。  
  
##  <a name="format"></a>CMFCAcceleratorKey::Format  
 将转换为其关联的字符串值的加速结构。  
  
```  
void Format(CString& str) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `str`  
 对引用`CString`对象，则该方法将翻译后的快捷键。  
  
### <a name="remarks"></a>备注  
 此方法检索关联的快捷键的字符串格式。 您可以设置的字符串格式[CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)对象使用构造函数或方法[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)。  
  
##  <a name="setaccelerator"></a>CMFCAcceleratorKey::SetAccelerator  
 设置的快捷键[CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)对象。  
  
```  
void SetAccelerator(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpAccel`  
 快捷方式键指向的指针。  
  
### <a name="remarks"></a>备注  
 使用此方法设置的快捷键`CMFCAcceleratorKey`如果您在创建时，未提供的快捷键`CMFCAcceleratorKey`。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager 类](../../mfc/reference/ckeyboardmanager-class.md)


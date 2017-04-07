---
title: "CMFCToolBarComboBoxEdit 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarComboBoxEdit class
- CMFCToolBarComboBoxEdit::PreTranslateMessage method
ms.assetid: 4789c34a-ce58-48ba-a26f-38748b601352
caps.latest.revision: 25
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 3c0f2ade3292fb238a227e881951604606baec79
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbarcomboboxedit-class"></a>CMFCToolBarComboBoxEdit 类
框架将使用`CMFCToolBarComboBoxEdit`类来创建类似于可编辑的组合框控件的工具栏按钮。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCToolBarComboBoxEdit : public CEdit  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit](#cmfctoolbarcomboboxedit)|构造 `CMFCToolBarComboBoxEdit` 对象。|  
|`CMFCToolBarComboBoxEdit::~CMFCToolBarComboBoxEdit`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|`CMFCToolBarComboBoxEdit::PreTranslateMessage`|翻译窗口消息之前被发送到[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函数。 (重写[cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|  
  
### <a name="remarks"></a>备注  
 从派生类`CMFCToolBarComboBoxEdit`类以自定义其编辑操作。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxtoolbarcomboboxbutton.h  
  
##  <a name="cmfctoolbarcomboboxedit"></a>CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit  
 构造 `CMFCToolBarComboBoxEdit` 对象。  
  
```  
CMFCToolBarComboBoxEdit(CMFCToolBarComboBoxButton& combo);
```  
  
### <a name="parameters"></a>参数  
 [in] `combo`  
 对引用[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)对象，它是包含一个组合框控件的工具栏按钮。  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCToolBarComboBoxEdit`类。 此代码段属于[IE 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_IEDemo #&5;](../../mfc/reference/codesnippet/cpp/cmfctoolbarcomboboxedit-class_1.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarComboBoxButton 类](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)


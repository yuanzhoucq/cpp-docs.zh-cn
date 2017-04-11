---
title: "UICheckState 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 04/03/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- afxwinforms/uicheckstate
dev_langs:
- C++
helpviewer_keywords:
- uicheckstate enumeration
ms.assetid: 2ac0098c-20e7-410c-9685-5ead5cb02b63
caps.latest.revision: 17
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
ms.sourcegitcommit: b943ef8dd652df061965fe81ecc9c08115636141
ms.openlocfilehash: d30ddee047597750d4627efee8ec8d9e01a520d6
ms.lasthandoff: 04/04/2017

---

# <a name="uicheckstate-enumeration"></a>UICheckState 枚举
描述该命令的用户界面项的复选状态。  
   
### <a name="syntax"></a>语法   
```  
public enum class 
{  
   [DefaultValue(typeid<Microsoft::VisualC::MFC::UICheckState>, "Checked")]  
   Unchecked,   
   Checked,   
   Indeterminate 
};  
```  
   
### <a name="remarks"></a>备注  
 [ICommandUI::Check](icommandui-interface.md#check)使用这些值来描述用户界面项的状态。    
 有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
   
### <a name="requirements"></a>要求  
 **标头︰** afxwinforms.h （在程序集 atlmfc\lib\mfcmifc80.dll 中定义）  


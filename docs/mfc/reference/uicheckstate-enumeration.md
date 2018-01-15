---
title: "UICheckState 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 04/03/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: afxwinforms/uicheckstate
dev_langs: C++
helpviewer_keywords: uicheckstate enumeration [MFC]
ms.assetid: 2ac0098c-20e7-410c-9685-5ead5cb02b63
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7feac12853066ad4971d98ce7cf25ec4d8a86fa8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
   
### <a name="requirements"></a>惠?  
 **标头：** afxwinforms.h （在程序集 atlmfc\lib\mfcmifc80.dll 中定义）  

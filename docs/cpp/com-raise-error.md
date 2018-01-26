---
title: _com_raise_error | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_raise_error
dev_langs: C++
helpviewer_keywords: _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 71a4be4ebf6029d0573aee71d74bf9faa241319f
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="comraiseerror"></a>_com_raise_error
**Microsoft 专用**  
  
 引发[_com_error](../cpp/com-error-class.md)以响应故障。  
  
## <a name="syntax"></a>语法  
  
```  
  
      void __stdcall _com_raise_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = 0  
);  
```  
  
#### <a name="parameters"></a>参数  
 `hr`  
 `HRESULT` 信息。  
  
 `perrinfo`  
 **IErrorInfo**对象。  
  
## <a name="remarks"></a>备注  
 `_com_raise_error`其定义中\<comdef.h >，可替换的用户编写相同的名称和原型的版本。 若要使用 `#import` 但不使用 C++ 异常处理，则可以执行此操作。 在这种情况下，用户版**_com_raise_error**可能决定做`longjmp`或显示一个消息框和暂停。 但不应返回用户版本，因为编译器 COM 支持代码不希望返回它。  
  
 你还可以使用[_set_com_error_handler](../cpp/set-com-error-handler.md)替换默认错误处理函数。  
  
 默认情况下，`_com_raise_error` 定义为：  
  
```  
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {  
   throw _com_error(hr, perrinfo);  
}  
```  
  
**结束 Microsoft 专用**  
  
## <a name="requirements"></a>惠?  
 **标头：** \<comdef.h >  
  
 **Lib:**如果**wchar_t is Native Type**编译器选项设置为 on，请使用对 comsuppw.lib 或 comsuppwd.lib。 如果**wchar_t is Native Type** ，请使用 comsupp.lib。 有关详细信息，请参阅 [/Zc:wchar_t（wchar_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。  
  
## <a name="see-also"></a>请参阅  
 [编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)   
 [_set_com_error_handler](../cpp/set-com-error-handler.md)
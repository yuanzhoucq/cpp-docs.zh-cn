---
title: "_com_error 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error
dev_langs:
- C++
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 53defbe6c686630791317fa20aca48414144eb91
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="comerror-class"></a>_com_error 类
**Microsoft 专用**  
  
 A`_com_error`对象表示检测到通过从类型库生成的标头文件中的错误处理包装函数或 COM 支持类之一的异常条件。 `_com_error`类封装`HRESULT`错误代码和任何关联`IErrorInfo Interface`对象。  
  
### <a name="construction"></a>构造  
  
|||  
|-|-|  
|[_com_error](../cpp/com-error-com-error.md)|构造 `_com_error` 对象。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator =](../cpp/com-error-operator-equal.md)|将现有 `_com_error` 对象赋给另一个对象。|  
  
### <a name="extractor-functions"></a>提取程序函数  
  
|||  
|-|-|  
|[错误](../cpp/com-error-error.md)|检索传递给构造函数的 `HRESULT`。|  
|[ErrorInfo](../cpp/com-error-errorinfo.md)|检索`IErrorInfo`对象传递给构造函数。|  
|[WCode](../cpp/com-error-wcode.md)|检索映射到封装的 `HRESULT` 中的 16 位错误代码。|  
  
### <a name="ierrorinfo-functions"></a>IErrorInfo 函数  
  
|||  
|-|-|  
|[说明](../cpp/com-error-description.md)|调用`IErrorInfo::GetDescription`函数。|  
|[HelpContext](../cpp/com-error-helpcontext.md)|调用`IErrorInfo::GetHelpContext`函数。|  
|[HelpFile](../cpp/com-error-helpfile.md)|调用`IErrorInfo::GetHelpFile`函数|  
|[Source](../cpp/com-error-source.md)|调用`IErrorInfo::GetSource`函数。|  
|[GUID](../cpp/com-error-guid.md)|调用`IErrorInfo::GetGUID`函数。|  
  
### <a name="format-message-extractor"></a>格式消息提取器  
  
|||  
|-|-|  
|[ErrorMessage](../cpp/com-error-errormessage.md)|检索字符串消息的 HRESULT 存储在`_com_error`对象。|  
  
### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo.wCode 到 HRESULT 映射器  
  
|||  
|-|-|  
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|映射 32 位`HRESULT`到 16 位`wCode`。|  
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|将 16 位 `wCode` 映射到 32 位 `HRESULT`。|  
  
**结束 Microsoft 专用**  
  
## <a name="requirements"></a>惠?  
 **标头：** \<comdef.h >  
  
 `Lib:`对 comsuppw.lib 或 comsuppwd.lib (请参阅[/zc: wchar_t （wchar_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)有关详细信息)  
  
## <a name="see-also"></a>请参阅  
 [编译器 COM 支持类](../cpp/compiler-com-support-classes.md)   
 [IErrorInfo 接口](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)
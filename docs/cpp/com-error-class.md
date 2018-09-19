---
title: _com_error 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error
dev_langs:
- C++
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dfbaf1f0c88eaeb71bc4dfbbf2dca72c8d07251e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117434"
---
# <a name="comerror-class"></a>_com_error 类

**Microsoft 专用**

一个 **_com_error**对象表示从类型库生成的标头文件中的错误处理包装器函数或其中一个 COM 支持类检测到的异常条件。 **_Com_error**类封装了 HRESULT 错误代码和任何关联`IErrorInfo Interface`对象。

### <a name="construction"></a>构造

|||
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|构造 **_com_error**对象。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator =](../cpp/com-error-operator-equal.md)|将现有 **_com_error**到另一个对象。|

### <a name="extractor-functions"></a>提取程序函数

|||
|-|-|
|[错误](../cpp/com-error-error.md)|检索传递给构造函数的 HRESULT。|
|[ErrorInfo](../cpp/com-error-errorinfo.md)|检索`IErrorInfo`对象传递给构造函数。|
|[WCode](../cpp/com-error-wcode.md)|检索映射到封装 HRESULT 的 16 位错误代码。|

### <a name="ierrorinfo-functions"></a>IErrorInfo 函数

|||
|-|-|
|[说明](../cpp/com-error-description.md)|调用`IErrorInfo::GetDescription`函数。|
|[HelpContext](../cpp/com-error-helpcontext.md)|调用`IErrorInfo::GetHelpContext`函数。|
|[HelpFile](../cpp/com-error-helpfile.md)|调用`IErrorInfo::GetHelpFile`函数|
|[Source](../cpp/com-error-source.md)|调用`IErrorInfo::GetSource`函数。|
|[GUID](../cpp/com-error-guid.md)|调用`IErrorInfo::GetGUID`函数。|

### <a name="format-message-extractor"></a>格式消息提取程序

|||
|-|-|
|[ErrorMessage](../cpp/com-error-errormessage.md)|HRESULT 存储中检索的字符串消息 **_com_error**对象。|

### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo.wCode 到 HRESULT 映射器

|||
|-|-|
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|将 32 位 HRESULT 映射到 16 位`wCode`。|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|映射 16 位`wCode`为 32 位 HRESULT。|

**结束 Microsoft 专用**

## <a name="requirements"></a>要求

**标头：** \<comdef.h >

`Lib:` comsuppw.lib 或 comsuppwd.lib (请参阅[/zc: wchar_t （wchar_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)有关详细信息)

## <a name="see-also"></a>请参阅

[编译器 COM 支持类](../cpp/compiler-com-support-classes.md)<br/>
[IErrorInfo 接口](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)
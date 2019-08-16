---
title: _com_error 类
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: 828a1ec68fef631700d5b64e6aeeec6660acf9a8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498748"
---
# <a name="_com_error-class"></a>_com_error 类

**Microsoft 专用**

**_Com_error**对象表示由类型库或某个 com 支持类生成的标头文件中的错误处理包装函数检测到的异常条件。 **_Com_error**类封装 HRESULT 错误代码和任何关联`IErrorInfo Interface`的对象。

### <a name="construction"></a>构造

|||
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|构造 **_com_error**对象。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator =](../cpp/com-error-operator-equal.md)|将现有的 **_com_error**对象分配给另一个对象。|

### <a name="extractor-functions"></a>提取程序函数

|||
|-|-|
|[错误](../cpp/com-error-error.md)|检索传递给构造函数的 HRESULT。|
|[ErrorInfo](../cpp/com-error-errorinfo.md)|检索传递`IErrorInfo`给构造函数的对象。|
|[WCode](../cpp/com-error-wcode.md)|检索映射到封装的 HRESULT 中的16位错误代码。|

### <a name="ierrorinfo-functions"></a>IErrorInfo 函数

|||
|-|-|
|[说明](../cpp/com-error-description.md)|调用`IErrorInfo::GetDescription`函数。|
|[HelpContext](../cpp/com-error-helpcontext.md)|调用`IErrorInfo::GetHelpContext`函数。|
|[HelpFile](../cpp/com-error-helpfile.md)|调用`IErrorInfo::GetHelpFile`函数|
|[源](../cpp/com-error-source.md)|调用`IErrorInfo::GetSource`函数。|
|[GUID](../cpp/com-error-guid.md)|调用`IErrorInfo::GetGUID`函数。|

### <a name="format-message-extractor"></a>格式消息提取程序

|||
|-|-|
|[ErrorMessage](../cpp/com-error-errormessage.md)|检索存储在 **_com_error**对象中的 HRESULT 的字符串消息。|

### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo wCode 到 HRESULT 映射器

|||
|-|-|
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|将32位 HRESULT 映射到16位`wCode`。|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|将16位`wCode`映射到32位 HRESULT。|

**结束 Microsoft 专用**

## <a name="requirements"></a>要求

**标头:** \<comdef.h >

`Lib:`comsuppw.lib 或 comsuppwd.lib (有关详细信息, 请参阅[/zc: wchar_t (Wchar_t 是本机类型)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)

## <a name="see-also"></a>请参阅

[编译器 COM 支持类](../cpp/compiler-com-support-classes.md)<br/>
[IErrorInfo 接口](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)
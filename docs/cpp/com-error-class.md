---
title: "_com_error 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_com_error 类"
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# _com_error 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 `_com_error` 对象表示在从类型生成的标头文件的错误处理的包装函数检测的异常条件库或由一个 COM 支持选件类。  `_com_error` 选件类来封装 `HRESULT` 错误代码和所有关联的 `IErrorInfo Interface` 对象。  
  
### 构造  
  
|||  
|-|-|  
|[\_com\_error](../cpp/com-error-com-error.md)|构造 `_com_error` 对象。|  
  
### 运算符  
  
|||  
|-|-|  
|[运算符\=](../cpp/com-error-operator-equal.md)|赋值存在的 `_com_error` 对象到另一个对象。|  
  
### 提取器功能  
  
|||  
|-|-|  
|[Error](../cpp/com-error-error.md)|索引传递到构造函数的 `HRESULT`。|  
|[IErrorInfo](../cpp/com-error-errorinfo.md)|恢复传递给构造函数的 `IErrorInfo` 对象。|  
|[WCode](../cpp/com-error-wcode.md)|检索映射到在封装的 `HRESULT` 16 位错误代码。|  
  
### IErrorInfo 功能  
  
|||  
|-|-|  
|[描述](../cpp/com-error-description.md)|调用`IErrorInfo::GetDescription`函数|  
|[HelpContext](../cpp/com-error-helpcontext.md)|调用`IErrorInfo::GetHelpContext`函数|  
|[HelpFile](../cpp/com-error-helpfile.md)|调用`IErrorInfo::GetHelpFile`函数|  
|[源](../cpp/com-error-source.md)|调用`IErrorInfo::GetSource`函数|  
|[GUID](../cpp/com-error-guid.md)|调用`IErrorInfo::GetGUID`函数|  
  
### 格式消息提取器  
  
|||  
|-|-|  
|[ErrorMessage](../cpp/com-error-errormessage.md)|检索存储在`_com_error` 对象中的HRESULT字符串信息。|  
  
### 为 HRESULT 映射器的 ExepInfo.wCode  
  
|||  
|-|-|  
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|将 32 位 `HRESULT` 映射到 16 位 `wCode`。|  
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|将 16 位 `wCode` 映射到 32 位 `HRESULT`。|  
  
## 结束 Microsoft 专用  
  
## 要求  
 `Header:` comdef.h  
  
 `Lib:` comsuppw.lib or comsuppwd.lib（有关更多信息，请参见[\/Zc:wchar\_t（wchar\_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)）  
  
## 请参阅  
 [编译器 COM 支持类](../cpp/compiler-com-support-classes.md)   
 [IErrorInfo Interface](http://msdn.microsoft.com/zh-cn/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)
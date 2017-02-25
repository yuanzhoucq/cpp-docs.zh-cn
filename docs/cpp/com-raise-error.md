---
title: "_com_raise_error | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_raise_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_com_raise_error 函数"
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# _com_raise_error
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 引发 [\_com\_error](../cpp/com-error-class.md) 以响应失败。  
  
## 语法  
  
```  
  
      void __stdcall _com_raise_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = 0  
);  
```  
  
#### 参数  
 `hr`  
 `HRESULT` 信息。  
  
 `perrinfo`  
 **IErrorInfo** 对象。  
  
## 备注  
 comdef.h 中定义的 `_com_raise_error` 可以替换为具有相同的名称和原型的用户编写的版本。  若要使用 `#import` 但不使用 C\+\+ 异常处理，则可以执行此操作。  在这种情况下，**\_com\_raise\_error** 的用户版本可能决定执行 `longjmp` 或显示消息框并暂停。  但不应返回用户版本，因为编译器 COM 支持代码不希望返回它。  
  
 还可以使用 [\_set\_com\_error\_handler](../cpp/set-com-error-handler.md) 替换默认的错误处理函数。  
  
 默认情况下，`_com_raise_error` 定义为：  
  
```  
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {  
   throw _com_error(hr, perrinfo);  
}  
```  
  
## 结束 Microsoft 专用  
  
## 要求  
 **标头：**comdef.h  
  
 **库：**如果启用“wchar\_t is Native Type”编译器选项，请使用 comsuppw.lib 或 comsuppwd.lib。  如果禁用“wchar\_t is Native Type”，请使用 comsupp.lib。  有关详细信息，请参阅 [\/Zc:wchar\_t（wchar\_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。  
  
## 请参阅  
 [编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)   
 [\_set\_com\_error\_handler](../cpp/set-com-error-handler.md)
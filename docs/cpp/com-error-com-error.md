---
title: _com_error::_com_error |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::_com_error
dev_langs:
- C++
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec16faa9881fc1c69dca5f8f39b8797cf0fcff0d
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942482"
---
# <a name="comerrorcomerror"></a>_com_error::_com_error
**Microsoft 专用**  
  
 构造 `_com_error` 对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
_com_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = NULL,  
   bool fAddRef=false) throw( );  

_com_error( const _com_error& that ) throw( );  
```  
  
#### <a name="parameters"></a>参数  
 *hr*  
 HRESULT 的信息。  
  
 *perrinfo*  
 `IErrorInfo` 对象。  
  
 `bool fAddRef=false`  
 导致构造函数非 null 值调用 AddRef`IErrorInfo`接口。 这可以在接口的所有权传入 `_com_error` 对象的常见情况下提供正确的引用计数，例如：  
  
```cpp 
throw _com_error(hr, perrinfo);  
```  
  
 如果不希望您的代码以将所有权转移给`_com_error`对象，并`AddRef`偏移需要`Release`中`_com_error`析构函数，构造对象，如下所示：  
  
```cpp 
_com_error err(hr, perrinfo, true);  
```  
  
 *的*  
 一个现有的 `_com_error` 对象。  
  
## <a name="remarks"></a>备注  
 第一个构造函数创建新的对象在给定的 HRESULT 和可选`IErrorInfo`对象。 第二个构造函数创建现有 `_com_error` 对象的副本。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_error 类](../cpp/com-error-class.md)
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
ms.openlocfilehash: c1389635c3ef026e8b3a7dfe13976cca58a15a82
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406713"
---
# <a name="comerrorcomerror"></a>_com_error::_com_error
**Microsoft 专用**  
  
 构造 **_com_error**对象。  
  
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
 导致构造函数非 null 值调用 AddRef`IErrorInfo`接口。 这提供了正确的引用计数的常见的情况下，其中在接口的所有权传递给 **_com_error**对象，例如：  
  
```cpp 
throw _com_error(hr, perrinfo);  
```  
  
 如果不希望您的代码以将所有权转移给 **_com_error**对象，并`AddRef`偏移需要`Release`中 **_com_error**析构函数中，构造对象作为如下所示：  
  
```cpp 
_com_error err(hr, perrinfo, true);  
```  
  
 *的*  
 将现有 **_com_error**对象。  
  
## <a name="remarks"></a>备注  
 第一个构造函数创建新的对象在给定的 HRESULT 和可选`IErrorInfo`对象。 第二个创建的现有副本 **_com_error**对象。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_error 类](../cpp/com-error-class.md)
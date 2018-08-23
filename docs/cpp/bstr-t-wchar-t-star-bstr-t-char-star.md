---
title: '_bstr_t:: wchar_t *，_bstr_t:: char* |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::wchar_t*
- _bstr_t::char*
dev_langs:
- C++
helpviewer_keywords:
- operator wchar_t* [C++]
- operator char* [C++]
ms.assetid: acd9f4a7-b427-42c2-aaae-acae21cab317
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ebe1f3ad7b0fc46e1edba013f4cc986f1771972d
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39409142"
---
# <a name="bstrtwchart-bstrtchar"></a>_bstr_t:: wchar_t *，_bstr_t:: char*
**Microsoft 专用**  
  
 将 BSTR 字符作为一个窄字符数组或宽字符数组返回。  
  
## <a name="syntax"></a>语法  
  
```  
operator const wchar_t*( ) const throw( );   
operator wchar_t*( ) const throw( );   
operator const char*( ) const;   
operator char*( ) const;  
```  
  
## <a name="remarks"></a>备注  
 这些运算符可用于提取由 `BSTR` 对象封装的字符数据。 为返回的指针赋予新值不会修改原始 BSTR 数据。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_bstr_t 类](../cpp/bstr-t-class.md)
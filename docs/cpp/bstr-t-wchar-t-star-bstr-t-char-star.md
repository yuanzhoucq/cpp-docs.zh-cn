---
title: '_bstr_t:: wchar_t *，_bstr_t:: char*'
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::wchar_t*
- _bstr_t::char*
helpviewer_keywords:
- operator wchar_t* [C++]
- operator char* [C++]
ms.assetid: acd9f4a7-b427-42c2-aaae-acae21cab317
ms.openlocfilehash: bfc149b0f0688bed567bf202fddb4ab2c3102630
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51325804"
---
# <a name="bstrtwchart-bstrtchar"></a>_bstr_t:: wchar_t\*，_bstr_t:: char\*

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
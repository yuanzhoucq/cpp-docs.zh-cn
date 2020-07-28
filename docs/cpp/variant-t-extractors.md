---
title: _variant_t 提取器
ms.date: 11/04/2016
f1_keywords:
- _variant_t.operatordouble
- operatorlong
- _variant_t::operator_bstr_t
- operatordouble
- _variant_t.operatorCY
- operatorCY
- _variant_t::operatorCY
- _variant_t::operatordouble
- operatorfloat
- operatorBYTE
- _variant_t.operatorDECIMAL
- _variant_t::operatorlong
- operatorIDispatch
- _variant_t.operatorBYTE
- operatorDECIMAL
- _variant_t.operator_bstr_t
- _variant_t::operatorDECIMAL
- _variant_t.operatorIUnknown
- _variant_t.operatorlong
- _variant_t::operatorIDispatch
- _variant_t::operatorIUnknown
- operatorIUnknown
- _variant_t.operatorbool
- _variant_t::operatorBYTE
- _variant_t.operatorfloat
- operator_bstr_t
- _variant_t::operatorbool
- operatorshort
- _variant_t::operatorshort
- _variant_t::operatorfloat
- _variant_t.operatorIDispatch
- _variant_t.operatorshort
helpviewer_keywords:
- extractors, _variant_t class
- operator CY
- operator IDispatch
- operator SHORT
- operator double
- operator long
- operator _bstr_t
- operator DECIMAL
- operator float
- operator bool
- operator BYTE
- operator IUnknown
ms.assetid: 33c1782f-045a-4673-9619-1d750efc83a9
ms.openlocfilehash: a1b7c713b5d82ff54250b622f2d4afe17abac468
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87185601"
---
# <a name="_variant_t-extractors"></a>_variant_t 提取器

**Microsoft 专用**

从封装的对象中提取数据 `VARIANT` 。

## <a name="syntax"></a>语法

```
operator short( ) const;
operator long( ) const;
operator float( ) const;
operator double( ) const;
operator CY( ) const;
operator _bstr_t( ) const;
operator IDispatch*( ) const;
operator bool( ) const;
operator IUnknown*( ) const;
operator DECIMAL( ) const;
operator BYTE( ) const;
operator VARIANT() const throw();
operator char() const;
operator unsigned short() const;
operator unsigned long() const;
operator int() const;
operator unsigned int() const;
operator __int64() const;
operator unsigned __int64() const;
```

## <a name="remarks"></a>备注

从封装的中提取原始数据 `VARIANT` 。 如果尚 `VARIANT` 不是正确的类型， `VariantChangeType` 则将用于尝试转换，并在失败时生成错误：

- **运算符 short （）** 提取 **`short`** 整数值。

- **operator long （）** 提取 **`long`** 整数值。

- **operator float （）** 提取 **`float`** 数值。

- **运算符 double （）** 提取 **`double`** 整数值。

- **OPERATOR CY （）** 提取 `CY` 对象。

- **operator bool （）** 提取 **`bool`** 值。

- **运算符 DECIMAL （）** 提取 `DECIMAL` 值。

- **OPERATOR BYTE （）** 提取 `BYTE` 值。

- **运算符 _bstr_t （）** 提取封装在对象中的字符串 `_bstr_t` 。

- **Operator IDispatch \* （）** 从封装的中提取调度接口指针 `VARIANT` 。 `AddRef`在得到的指针上调用，因此由您调用 `Release` 来释放它。

- **Operator IUnknown \* （）** 从封装的中提取 COM 接口指针 `VARIANT` 。 `AddRef`在得到的指针上调用，因此由您调用 `Release` 来释放它。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_variant_t 类](../cpp/variant-t-class.md)

---
title: _variant_t::ChangeType
ms.date: 11/04/2016
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
ms.openlocfilehash: c2283158856a6781ab2e12c51f4e2ad0e4f1d531
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750726"
---
# <a name="_variant_tchangetype"></a>_variant_t::ChangeType

**微软特定**

将`_variant_t`对象的类型更改为指示`VARTYPE`的 。

## <a name="syntax"></a>语法

```cpp
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>参数

*vartype*<br/>
此`VARTYPE``_variant_t`对象的 。

*pSrc*<br/>
指向要转换的 `_variant_t` 对象的指针。 如果此值为 NULL，则转换将就地完成。

## <a name="remarks"></a>备注

此成员函数将`_variant_t`对象转换为指示`VARTYPE`的 。 如果*pSrc*为 NULL，则转换就位，否则`_variant_t`此对象将从*pSrc*复制，然后转换。

**结束微软特定**

## <a name="see-also"></a>请参阅

[_variant_t类](../cpp/variant-t-class.md)

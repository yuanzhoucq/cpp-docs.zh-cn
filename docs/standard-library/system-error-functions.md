---
title: '&lt;system_error&gt; 函数 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- system_error/std::generic_category
- system_error/std::make_error_code
- system_error/std::make_error_condition
- system_error/std::system_category
ms.assetid: 57d6f15f-f0b7-4e2f-80fe-31d3c320ee33
caps.latest.revision: 11
manager: ghogen
helpviewer_keywords:
- std::generic_category
- std::make_error_code
- std::make_error_condition
- std::system_category
ms.openlocfilehash: 988c3580d1cd9a66e1b396fc83bd20fd3f4a115e
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="ltsystemerrorgt-functions"></a>&lt;system_error&gt; 函数

||||
|-|-|-|
|[generic_category](#generic_category)|[make_error_code](#make_error_code)|[make_error_condition](#make_error_condition)|
|[system_category](#system_category)|

## <a name="generic_category"></a>generic_category

表示一般错误的类别。

```cpp
extern const error_category& generic_category();
```

### <a name="remarks"></a>备注

`generic_category`对象是实现的[error_category](../standard-library/error-category-class.md)。

## <a name="make_error_code"></a>make_error_code

创建错误代码对象。

```cpp
error_code make_error_code(generic_errno _Errno);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`_Errno`|要存储在错误代码对象中的枚举值。|

### <a name="return-value"></a>返回值

错误代码对象。

### <a name="remarks"></a>备注

## <a name="make_error_condition"></a>make_error_condition

创建错误条件对象。

```cpp
error_condition make_error_condition(generic_errno _Errno);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`_Errno`|要存储在错误条件对象中的枚举值。|

### <a name="return-value"></a>返回值

错误条件对象。

### <a name="remarks"></a>备注

## <a name="system_category"></a>  system_category

表示因低级别系统溢出而引起的错误类别。

```cpp
extern const error_category& system_category();
```

### <a name="remarks"></a>备注

`system_category`对象是实现的[error_category](../standard-library/error-category-class.md)。

## <a name="see-also"></a>请参阅

[<system_error>](../standard-library/system-error.md)<br/>

---
title: uuid (C++)
ms.date: 11/04/2016
f1_keywords:
- uuid_cpp
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
ms.openlocfilehash: c121ad99dfbe0021a263f324ccdb9a95441bba33
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511652"
---
# <a name="uuid-c"></a>uuid (C++)

**Microsoft 专用**

编译器将 GUID 附加到类或结构声明或定义 （完整的 COM 对象定义仅） 与**uuid**属性。

## <a name="syntax"></a>语法

```
__declspec( uuid("ComObjectGUID") ) declarator
```

## <a name="remarks"></a>备注

**Uuid**属性采用字符串作为其参数。 此字符串名称中带有或不带的普通注册表格式的 GUID **{}** 分隔符。 例如：

```cpp
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;
```

此特性可应用于重新声明。 这允许系统标头提供接口的定义，如`IUnknown`，和其他标头中的重新声明 (如\<comdef.h >) 提供 GUID。

关键字[__uuidof](../cpp/uuidof-operator.md)可用于检索 GUID 附加到的用户定义的类型的常量。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)
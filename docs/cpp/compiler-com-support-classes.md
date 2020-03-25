---
title: 编译器 COM 支持类
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: a8b0845fdfa96c1cb4b8b67e9d39169d9f4d3737
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189697"
---
# <a name="compiler-com-support-classes"></a>编译器 COM 支持类

**Microsoft 专用**

标准类用于支持某些 COM 类型。 类在 \<comdef.h > 和从类型库生成的标头文件中定义。

|类|目的|
|-----------|-------------|
|[_bstr_t](../cpp/bstr-t-class.md)|包装 `BSTR` 类型，以提供有用的运算符和方法。|
|[_com_error](../cpp/com-error-class.md)|定义在大多数失败中由[_com_raise_error](../cpp/com-raise-error.md)引发的错误对象。|
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|封装 COM 接口指针，并自动执行对 `AddRef`、`Release`和 `QueryInterface`所需的调用。|
|[_variant_t](../cpp/variant-t-class.md)|包装 `VARIANT` 类型，以提供有用的运算符和方法。|

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[编译器 COM 支持](../cpp/compiler-com-support.md)<br/>
[编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)<br/>
[C++ 语言参考](../cpp/cpp-language-reference.md)

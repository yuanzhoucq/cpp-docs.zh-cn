---
title: 编译器 COM 支持类
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: 066fe797bc500625e96e027777a70f278b88cddb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479659"
---
# <a name="compiler-com-support-classes"></a>编译器 COM 支持类

**Microsoft 专用**

标准类用于支持某些 COM 类型。 在定义了类\<comdef.h > 并从类型库生成的标头文件。

|类|目标|
|-----------|-------------|
|[_bstr_t](../cpp/bstr-t-class.md)|包装 `BSTR` 类型，以提供有用的运算符和方法。|
|[_com_error](../cpp/com-error-class.md)|定义引发的错误对象[_com_raise_error](../cpp/com-raise-error.md)在大多数失败中。|
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|封装 COM 接口指针，并自动执行对所需的调用`AddRef`， `Release`，和`QueryInterface`。|
|[_variant_t](../cpp/variant-t-class.md)|包装 `VARIANT` 类型，以提供有用的运算符和方法。|

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器 COM 支持](../cpp/compiler-com-support.md)<br/>
[编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)<br/>
[C++ 语言参考](../cpp/cpp-language-reference.md)
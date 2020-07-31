---
title: 编译器 COM 支持
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: 9a5961049cbc54c94cec5b444e2d98f013dda932
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233777"
---
# <a name="compiler-com-support"></a>编译器 COM 支持

**Microsoft 专用**

Microsoft c + + 编译器可以直接读取组件对象模型（COM）类型库，并将内容转换为可在编译中包括的 c + + 源代码。 语言扩展可用于在客户端为桌面应用程序提供 COM 编程。

通过使用[#import 预处理器指令](../preprocessor/hash-import-directive-cpp.md)，编译器可以读取类型库，并将其转换为 c + + 头文件（将 COM 接口描述为类）。 提供了一组 `#import` 特性来实现对生成的类型库头文件的内容的用户控制。

可以使用[__declspec](../cpp/declspec.md)扩展属性[uuid](../cpp/uuid-cpp.md)为 COM 对象分配全局唯一标识符（GUID）。 关键字[__uuidof](../cpp/uuidof-operator.md)可用于提取与 COM 对象关联的 GUID。 另一个 **`__declspec`** 属性（ [property](../cpp/property-cpp.md)）可用于指定 `get` `set` COM 对象的数据成员的和方法。

提供一组 COM 支持全局函数和类以支持 `VARIANT` 和 `BSTR` 类型，实现智能指针，并封装引发的错误对象 `_com_raise_error` ：

- [编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器 COM 支持类](../cpp/compiler-com-support-classes.md)<br/>
[编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)

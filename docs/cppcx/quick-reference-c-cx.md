---
title: 快速参考 (C + + /cli CX) |Microsoft 文档
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: ba457195-26e5-43aa-b99d-24a871e550f4
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 830c27d89e427e2ea36a68d891aac0ebadcf3f21
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092553"
---
# <a name="quick-reference-ccx"></a>快速参考 (C++/CX)
Windows 运行时支持，只在可信操作系统环境中执行的使用授权的函数、 数据类型和设备，以及通过 Microsoft 应用商店分布的通用 Windows 平台 (UWP) 应用程序。 C + + /cli CX 简化对 Windows 运行时编写应用程序。 本文仅作为快速参考;有关更完整的文档，请参阅[类型系统](../cppcx/type-system-c-cx.md)和[运行时平台的组件扩展](http://go.microsoft.com/fwlink/p/?linkid=228720)。  
  
 在命令行上生成时，使用 **/ZW**编译器选项生成的 UWP 应用或 Windows 运行时组件。 若要访问 Windows 运行时的声明，它们在 Windows 运行时元数据 (.winmd) 文件中定义，指定`#using`指令或 **/FU**编译器选项。 当你创建的 UWP 应用项目时，默认情况下的 Visual Studio 设置这些选项，并添加对所有 Windows 运行时库的引用。  
  
## <a name="quick-reference"></a>快速参考  
  
|概念|标准 C++|C++/CX|备注|  
|-------------|--------------------|------------------------------------------------------------------|-------------|  
|基本类型|C++ 基础类型。|C + + /cli CX 实现在 Windows 运行时中定义的基础类型的基础类型。|`default`命名空间包含 C + + /cli CX 内置的基础类型。 编译器隐式映射 C + + /cli CX 到标准 c + + 类型的基础类型。<br /><br /> `Platform`的命名空间的系列包含实现基本 Windows 运行时类型的类型。|  
||`bool`|`bool`|8 位布尔值。|  
||`__wchar_t`|`char16`|表示 Unicode (UTF-16) 码位的 16 位非数字值。|  
||`short`<br /><br /> `unsigned short`|`int16`<br /><br /> `uint16`|16 位带符号整数。<br /><br /> 16 位无符号整数。|  
||`int`<br /><br /> `unsigned int`|`int`<br /><br /> `uint32`|32 位带符号整数。<br /><br /> 32 位无符号整数。|  
||`long long` - 或 - `__int64`<br /><br /> `unsigned long long`|`int64`<br /><br /> `uint64`|64 位带符号整数。<br /><br /> 64 位无符号整数。|  
||`float, double`|`float32, float64`|32 位或 64 位 IEEE 754 浮点数。|  
||`enum {}`|`enum class {}`<br /><br /> -或-<br /><br /> `enum struct {}`|32 位枚举。|  
||（不适用）|`Platform::Guid`|`Platform` 命名空间中的 128 位非数字值 (GUID)。|  
||`std::time_get`|`Windows::Foundation::DateTime`|日期-时间结构。|  
||（不适用）|`Windows::Foundation::TimeSpan`|timespan 结构。|  
||（不适用）|`Platform::Object^`|引用计数基对象的 Windows 运行时类型系统的 c + + 视图中。|  
||`std::wstring`<br /><br /> `L"..."`|`Platform::String^`|`Platform::String^` 是用来表示文本的 Unicode 字符的引用计数不可变序列。|  
|指针|指向对象的指针 (`*`)：<br /><br /> `std::shared_ptr`|句柄到对象 (`^`，发音为“hat”)：<br /><br /> *T^ 标识符*|所有 Windows 运行时类都通过使用句柄到对象修饰符都声明。 使用箭头 (`->`) 类成员访问运算符访问对象的成员。<br /><br /> Hat 修饰符意味着"指向自动引用的 Windows 运行时对象计数。" 更确切地说，句柄到对象声明编译器应插入代码以便自动管理对象的引用计数，如果引用计数变为零，则删除对象。|  
|参考|引用对象 (`&`)：<br /><br /> *T* `&` *identifier*|跟踪引用 (`%`)：<br /><br /> *T* `%` *identifier*|仅 Windows 运行时类型可以声明使用跟踪引用修饰符。 使用点 (`.`) 类成员访问运算符访问对象的成员。<br /><br /> 跟踪引用表示"对自动引用计数的 Windows 运行时对象的引用。" 更确切地说，跟踪引用声明编译器应插入代码以便自动管理对象的引用计数，如果引用计数变为零，则删除对象。|  
|动态类型声明|`new`|`ref new`|分配的 Windows 运行时对象，然后返回该对象的句柄。|  
|对象生存期管理|`delete` *identifier*<br /><br /> `delete[]`  *identifier*|（调用析构函数。）|生存期由引用计数确定。 调用删除会调用析构函数，但它本身不释放内存。|  
|数组声明|*T 标识符* `[]`<br /><br /> `std::array` *identifier*|`Array<` *T* `^>^` *identifier* `(` *size* `)`<br /><br /> -或-<br /><br /> `WriteOnlyArray<` *T* `^>`  *identifier* `(` *size* `)`|声明类型 T^ 的一维可修改或只写数组。 该数组本身也是必须用句柄到对象修饰符声明的引用计数对象。<br /><br /> （数组声明使用位于 `Platform` 命名空间中的模板标头类。）|  
|类声明|`class`  *identifier* `{}`<br /><br /> `struct` *identifier* `{}`|`ref class` *identifier* `{}`<br /><br /> `ref struct` *identifier* `{}`|声明具有默认私有可访问性的运行时类。<br /><br /> 声明具有默认公共可访问性的运行时类。|  
|结构声明|`struct` *identifier* `{}`<br /><br /> （即，纯旧数据结构 (POD)）|`value class` *identifier* `{}`<br /><br /> `value struct` *identifier* `{}`|声明具有默认私有可访问性的 POD 结构。<br /><br /> 值类可在 Windows 元数据中表示，但标准 C++ 类不能。<br /><br /> 声明具有默认公共可访问性的 POD 结构。<br /><br /> 值结构可在 Windows 元数据中表示，但标准 C++ 结构不能。|  
|接口声明|只包含纯虚函数的抽象类。|`interface class` *identifier* `{}`<br /><br /> `interface struct` *identifier* `{}`|声明具有默认私有可访问性的接口。<br /><br /> 声明具有默认公共可访问性的接口。|  
|委托|`std::function`|`public delegate` *返回类型* *delegate-type-identifier* `(` *[ parameters ]* `);`|声明一个可以象函数调用一样被调用的对象。|  
|Event — 事件|（不适用）|`event` *delegate-type-identifier* *event-identifier* `;`<br /><br /> *delegate-type-identifier* *delegate-identifier* = `ref new`*delegate-type-identifier*`( this`*[, parameters]*`);`<br /><br /> *event-identifier* `+=` *delegate-identifier* `;`<br /><br /> -或-<br /><br /> `EventRegistrationToken` *token-identifier* = *obj*`.`*event-identifier*`+=`*delegate-identifier*`;`<br /><br /> -或-<br /><br /> `auto` *令牌标识符* = *obj*。*事件标识符*`::add(`*委托标识符*`);`<br /><br /> *obj* `.` *event-identifier* `-=` *token-identifier* `;`<br /><br /> -或-<br /><br /> *obj* `.` *event-identifier* `::remove(` *token-identifier* `);`|声明一个事件对象，它存储在事件发生时被调用的事件处理程序（委托）的集合。<br /><br /> 创建事件处理程序。<br /><br /> 添加事件处理程序。<br /><br /> 添加事件处理程序会返回事件标记 (*token-identifier*)。 如果要显式移除事件处理程序，则必须保存事件标记供以后使用。<br /><br /> 移除事件处理程序。<br /><br /> 若要移除事件处理程序，必须指定在添加事件处理程序时保存的事件标记。|  
|属性|（不适用）|`property` *T* *标识符*；<br /><br /> `property` *T* *identifier* `[` *索引* `];`<br /><br /> `property` *T* `default[` *索引* `];`|声明类或对象成员函数可通过用于访问数据成员或索引数组元素的同一语法来访问。<br /><br /> 在类或对象成员函数上声明属性。<br /><br /> 在对象成员函数上声明索引属性。<br /><br /> 在类成员函数上声明索引属性。|  
|参数化类型|模板|`generic <typename` *T* `> interface class` *identifier* `{}`<br /><br /> `generic <typename` *T* `> delegate` *[return-type]* *delegate-identifier* `() {}`|声明参数化的接口类。<br /><br /> 声明参数化的委托。|  
|可以为 null 的值类型|`boost::optional<T>`|[Platform:: ibox \<T >](../cppcx/platform-ibox-interface.md)|使标量类型和值结构的变量能够具有值 `nullptr`。|  
  
## <a name="see-also"></a>请参阅  
 [Visual c + + 语言参考](../cppcx/visual-c-language-reference-c-cx.md)
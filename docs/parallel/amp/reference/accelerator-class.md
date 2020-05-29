---
title: accelerator 类
ms.date: 11/04/2016
f1_keywords:
- AMPRT/accelerator
- AMPRT/Concurrency::accelerator::accelerator
- AMPRT/Concurrency::accelerator::create_view
- AMPRT/Concurrency::accelerator::get_all
- AMPRT/Concurrency::accelerator::get_auto_selection_view
- AMPRT/Concurrency::accelerator::get_dedicated_memory
- AMPRT/Concurrency::accelerator::get_default_cpu_access_type
- AMPRT/Concurrency::accelerator::get_default_view
- AMPRT/Concurrency::accelerator::get_description
- AMPRT/Concurrency::accelerator::get_device_path
- AMPRT/Concurrency::accelerator::get_has_display
- AMPRT/Concurrency::accelerator::get_is_debug
- AMPRT/Concurrency::accelerator::get_is_emulated
- AMPRT/Concurrency::accelerator::get_supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::get_supports_double_precision
- AMPRT/Concurrency::accelerator::get_supports_limited_double_precision
- AMPRT/Concurrency::accelerator::get_version
- AMPRT/Concurrency::accelerator::set_default
- AMPRT/Concurrency::accelerator::set_default_cpu_access_type
- AMPRT/Concurrency::accelerator::cpu_accelerator
- AMPRT/Concurrency::accelerator::dedicated_memory
- AMPRT/Concurrency::accelerator::default_accelerator
- AMPRT/Concurrency::accelerator::default_cpu_access_type
- AMPRT/Concurrency::accelerator::default_view
- AMPRT/Concurrency::accelerator::description
- AMPRT/Concurrency::accelerator::device_path
- AMPRT/Concurrency::accelerator::direct3d_ref
- AMPRT/Concurrency::accelerator::direct3d_warp
- AMPRT/Concurrency::accelerator::has_display
- AMPRT/Concurrency::accelerator::is_debug
- AMPRT/Concurrency::accelerator::is_emulated
- AMPRT/Concurrency::accelerator::supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::supports_double_precision
- AMPRT/Concurrency::accelerator::supports_limited_double_precision
- AMPRT/Concurrency::accelerator::version
helpviewer_keywords:
- accelerator class
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
ms.openlocfilehash: 72a570ab28696730f835c42748a6ea12b865ca55
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427481"
---
# <a name="accelerator-class"></a>accelerator 类

加速器是针对数据并行计算进行优化的硬件功能。 加速器可以是连接到 PCIe 总线的设备（如 GPU），也可以是主 CPU 上的扩展指令集。

## <a name="syntax"></a>语法

```cpp
class accelerator;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[快捷键构造函数](#ctor)|初始化 `accelerator` 类的新实例。|
|[~ 加速器析构函数](#ctor)|销毁 `accelerator` 的对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[create_view](#create_view)|在此快捷键上创建并返回一个 `accelerator_view` 对象。|
|[get_all](#get_all)|返回表示所有可用加速器的 `accelerator` 对象的向量。|
|[get_auto_selection_view](#get_auto_selection_view)|返回 `accelerator_view`自动选择。|
|[get_dedicated_memory](#get_dedicated_memory)|返回 `accelerator`的专用内存（以 kb 为单位）。|
|[get_default_cpu_access_type](#get_default_cpu_access_type)|返回在此快捷键上创建的缓冲区的默认[access_type](concurrency-namespace-enums-amp.md#access_type) 。|
|[get_default_view](#get_default_view)|返回与 `accelerator`关联的默认 `accelerator_view` 对象。|
|[get_description](#get_description)|返回 `accelerator` 设备的简短说明。|
|[get_device_path](#get_device_path)|返回设备的路径。|
|[get_has_display](#get_has_display)|确定是否将 `accelerator` 附加到显示器。|
|[get_is_debug](#get_is_debug)|确定 `accelerator` 是否为广泛的错误报告启用了调试层。|
|[get_is_emulated](#get_is_emulated)|确定是否模拟 `accelerator`。|
|[get_supports_cpu_shared_memory](#get_supports_cpu_shared_memory)|确定 `accelerator` 是否支持共享内存|
|[get_supports_double_precision](#get_supports_double_precision)|确定是否将 `accelerator` 附加到显示器。|
|[get_supports_limited_double_precision](#get_supports_limited_double_precision)|确定 `accelerator` 是否对双精度算术的支持有限。|
|[get_version](#get_version)|返回 `accelerator`的版本。|
|[set_default](#set_default)|返回默认快捷键的路径。|
|[set_default_cpu_access_type](#set_default_cpu_access_type)|为在此 `accelerator`上进行的数组和隐式内存分配设置默认 CPU [access_type](concurrency-namespace-enums-amp.md#access_type)。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[operator!=](#operator_neq)|将此 `accelerator` 对象与另一个对象进行比较，如果二者相同，则返回**false** ;否则，返回**true**。|
|[operator=](#operator_eq)|将指定 `accelerator` 对象的内容复制到此对象。|
|[operator==](#operator_eq_eq)|将此 `accelerator` 对象与另一个对象进行比较，如果相等，则返回**true** ;否则，返回**false**。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[cpu_accelerator](#cpu_accelerator)|获取 CPU `accelerator`的字符串常量。|
|[dedicated_memory](#dedicated_memory)|获取 `accelerator`的专用内存（以 kb 为单位）。|
|[default_accelerator](#default_accelerator)|获取默认 `accelerator`的字符串常量。|
|[default_cpu_access_type](#default_cpu_access_type)|获取或设置在此 `accelerator`上进行的数组和隐式内存分配的默认 CPU [access_type](concurrency-namespace-enums-amp.md#access_type)。|
|[default_view](#default_view)|获取与 `accelerator`关联的默认 `accelerator_view` 对象。|
|[description](#description)|获取 `accelerator` 设备的简短说明。|
|[device_path](#device_path)|获取设备的路径。|
|[direct3d_ref](#direct3d_ref)|获取 Direct3D 引用 `accelerator`的字符串常量。|
|[direct3d_warp](#direct3d_warp)|获取 `accelerator` 对象的字符串常量，可用于在使用流式处理 SIMD C++扩展（SSE）的多核 cpu 上执行 AMP 代码。|
|[has_display](#has_display)|获取一个布尔值，该值指示是否将 `accelerator` 附加到显示器。|
|[is_debug](#is_debug)|指示 `accelerator` 是否为广泛的错误报告启用了调试层。|
|[is_emulated](#is_emulated)|指示是否模拟 `accelerator`。|
|[supports_cpu_shared_memory](#supports_cpu_shared_memory)|指示 `accelerator` 是否支持共享内存。|
|[supports_double_precision](#supports_double_precision)|指示快捷键是否支持双精度运算。|
|[supports_limited_double_precision](#supports_limited_double_precision)|指示快捷键是否对双精度算术的支持有限。|
|[version](#version)|获取 `accelerator` 的版本。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`accelerator`

## <a name="remarks"></a>备注

加速器是针对数据并行计算进行优化的硬件功能。 加速器通常是离散的 GPU，但也可以是虚拟主机端实体，如 DirectX 引用设备、弯曲（通过 SSE 指令加速的 CPU 端设备）或 CPU 本身。

可以通过枚举可用设备，或通过获取默认设备、引用设备或变形设备来构造 `accelerator` 对象。

## <a name="requirements"></a>要求

**标头：** amprt

**命名空间：** 并发

## <a name="dtor"></a></a> ~ 加速器

销毁 `accelerator` 的对象。

```cpp
~accelerator();
```

### <a name="return-value"></a>返回值

## <a name="ctor"></a>键

初始化[快捷键类](accelerator-class.md)的新实例。

```cpp
accelerator();

explicit accelerator(const std::wstring& _Device_path);

accelerator(const accelerator& _Other);
```

### <a name="parameters"></a>parameters

*_Device_path*<br/>
物理设备的路径。

*_Other*<br/>
要复制的快捷键。

## <a name="cpu_accelerator"></a>cpu_accelerator

获取 CPU 快捷键的字符串常数。

```cpp
static const wchar_t cpu_accelerator[];
```

## <a name="create_view"></a>create_view

使用指定的排队模式，在快捷键上创建并返回一个 `accelerator_view` 对象。 如果未指定队列模式，新 `accelerator_view` 将使用[queuing_mode：：即时](concurrency-namespace-enums-amp.md#queuing_mode)排队模式。

```cpp
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>parameters

*qmode*<br/>
排队模式。

### <a name="return-value"></a>返回值

使用指定队列的模式，在此快捷键上创建的新 `accelerator_view` 对象。

## <a name="dedicated_memory"></a>dedicated_memory

获取 `accelerator`的专用内存（以 kb 为单位）。

```cpp
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;
```

## <a name="default_accelerator"></a>default_accelerator

获取默认 `accelerator`的字符串常量。

```cpp
static const wchar_t default_accelerator[];
```

## <a name="default_cpu_access_type"></a>default_cpu_access_type

在此 `accelerator`上进行的数组和隐式内存分配的默认 cpu [access_type](concurrency-namespace-enums-amp.md#access_type)。

```cpp
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;
```

## <a name="default_view"></a>default_view

获取与 `accelerator`关联的默认快捷键视图。

```cpp
__declspec(property(get= get_default_view)) accelerator_view default_view;
```

## <a name="description"></a>2008

获取 `accelerator` 设备的简短说明。

```cpp
__declspec(property(get= get_description)) std::wstring description;
```

## <a name="device_path"></a>device_path

获取快捷键的路径。 该路径在系统上是唯一的。

```cpp
__declspec(property(get= get_device_path)) std::wstring device_path;
```

## <a name="direct3d_ref"></a>direct3d_ref

获取 Direct3D 引用快捷键的字符串常数。

```cpp
static const wchar_t direct3d_ref[];
```

## <a name="direct3d_warp"></a>direct3d_warp

获取 `accelerator` 对象的字符串常量，可用于在使用流式处理 SIMD 扩展C++ （SSE）的多核 cpu 上执行 AMP 代码。

```cpp
static const wchar_t direct3d_warp[];
```

## <a name="get_all"></a>get_all

返回表示所有可用加速器的 `accelerator` 对象的向量。

```cpp
static inline std::vector<accelerator> get_all();
```

### <a name="return-value"></a>返回值

可用快捷键的矢量

## <a name="get_auto_selection_view"></a>get_auto_selection_view

返回自动选择 accelerator_view，当指定为 parallel_for_each 目标时，将导致目标 accelerator_view 执行运行时自动选择的 parallel_for_each 内核。 对于所有其他目的，此方法返回的 accelerator_view 与默认快捷键的默认 accelerator_view 相同

```cpp
static accelerator_view __cdecl get_auto_selection_view();
```

### <a name="return-value"></a>返回值

自动选择 accelerator_view。

## <a name="get_dedicated_memory"></a>get_dedicated_memory

返回 `accelerator`的专用内存（以 kb 为单位）。

```cpp
size_t get_dedicated_memory() const;
```

### <a name="return-value"></a>返回值

`accelerator` 的专用内存（单位为 KB）。

## <a name="get_default_cpu_access_type"></a>get_default_cpu_access_type

获取在此快捷键上创建的缓冲区的默认 cpu access_type

```cpp
access_type get_default_cpu_access_type() const;
```

### <a name="return-value"></a>返回值

在此快捷键上创建的缓冲区的默认 cpu access_type。

## <a name="get_default_view"></a>get_default_view

返回与 `accelerator`关联的默认 `accelerator_view` 对象。

```cpp
accelerator_view get_default_view() const;
```

### <a name="return-value"></a>返回值

与 `accelerator_view` 关联的默认 `accelerator` 对象。

## <a name="get_description"></a>get_description

返回 `accelerator` 设备的简短说明。

```cpp
std::wstring get_description() const;
```

### <a name="return-value"></a>返回值

`accelerator` 设备的简短说明。

## <a name="get_device_path"></a>get_device_path

返回快捷键的路径。 该路径在系统上是唯一的。

```cpp
std::wstring get_device_path() const;
```

### <a name="return-value"></a>返回值

系统范围的唯一设备实例路径。

## <a name="get_has_display"></a>get_has_display

返回一个布尔值，该值指示 `accelerator` 是否可以输出到显示器。

```cpp
bool get_has_display() const;
```

### <a name="return-value"></a>返回值

如果 `accelerator` 可以输出到显示，**则为 true** ;否则**为 false**。

## <a name="get_is_debug"></a>get_is_debug

确定 `accelerator` 是否为广泛的错误报告启用了调试层。

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>返回值

如果 `accelerator` 为广泛的错误报告启用了调试层，**则为 true** 。 否则为 **false**。

## <a name="get_is_emulated"></a>get_is_emulated

确定是否模拟 `accelerator`。

```cpp
bool get_is_emulated() const;
```

### <a name="return-value"></a>返回值

如果模拟 `accelerator`，**则为 true** 。 否则为 **false**。

## <a name="get_supports_cpu_shared_memory"></a>get_supports_cpu_shared_memory

返回一个布尔值，该值指示快捷键是否支持可由加速器和 CPU 访问的内存。

```cpp
bool get_supports_cpu_shared_memory() const;
```

### <a name="return-value"></a>返回值

如果加速器支持 CPU 共享内存，则为**true** ;否则**为 false**。

## <a name="get_supports_double_precision"></a>get_supports_double_precision

返回一个布尔值，该值指示快捷键是否支持双精度算术运算，包括在**int**和**double**之间进行的融合乘加法（FMA）、除法、倒数和强制转换

```cpp
bool get_supports_double_precision() const;
```

### <a name="return-value"></a>返回值

如果快捷键支持双精度数学计算，则为**true** ;否则**为 false**。

## <a name="get_supports_limited_double_precision"></a>get_supports_limited_double_precision

返回一个布尔值，指示快捷键是否限制了对双精度算术的支持。 如果加速器仅支持有限限制，则不支持在**int**和**double**之间进行带外乘法加法（FMA）、除法、倒数和强制转换。

```cpp
bool get_supports_limited_double_precision() const;
```

### <a name="return-value"></a>返回值

如果快捷键对双精度算术的支持有限，则为**true** ;否则**为 false**。

## <a name="get_version"></a>get_version

返回 `accelerator`的版本。

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>返回值

`accelerator` 的版本。

## <a name="has_display"></a>has_display

获取一个布尔值，该值指示 `accelerator` 是否可以输出到显示器。

```cpp
__declspec(property(get= get_has_display)) bool has_display;
```

## <a name="is_debug"></a>is_debug

获取一个布尔值，该值指示 `accelerator` 是否为广泛的错误报告启用了调试层。

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="is_emulated"></a>is_emulated

获取一个布尔值，该值指示是否模拟 `accelerator`。

```cpp
__declspec(property(get= get_is_emulated)) bool is_emulated;
```

## <a name="operator_neq"></a>operator！ =

将此 `accelerator` 对象与另一个对象进行比较，如果二者相同，则返回**false** ;否则，返回**true**。

```cpp
bool operator!= (const accelerator& _Other) const;
```

### <a name="parameters"></a>parameters

*_Other*<br/>
与此对象相比较的 `accelerator` 对象。

### <a name="return-value"></a>返回值

如果两个 `accelerator` 对象相同，则为 false; 否则为**false** 。否则**为 true**。

## <a name="operator_eq"></a>operator =

将指定 `accelerator` 对象的内容复制到此对象。

```cpp
accelerator& operator= (const accelerator& _Other);
```

### <a name="parameters"></a>parameters

*_Other*<br/>
要从中进行复制的 `accelerator` 对象。

### <a name="return-value"></a>返回值

对此 `accelerator` 对象的引用。

## <a name="operator_eq_eq"></a>operator = =

将此 `accelerator` 对象与另一个对象进行比较，如果相等，则返回**true** ;否则，返回**false**。

```cpp
bool operator== (const accelerator& _Other) const;
```

### <a name="parameters"></a>parameters

*_Other*<br/>
与此对象相比较的 `accelerator` 对象。

### <a name="return-value"></a>返回值

如果其他 `accelerator` 对象与此 `accelerator` 对象相同，则为**true** ;否则**为 false**。

## <a name="set_default"></a>set_default

设置要用于任何隐式使用默认快捷键的操作的默认快捷键。 仅当运行时选择的默认快捷键未在隐式使用默认快捷键的操作中使用时，此方法才会成功。

```cpp
static inline bool set_default(std::wstring _Path);
```

### <a name="parameters"></a>parameters

*_Path*<br/>
加速器的路径。

### <a name="return-value"></a>返回值

如果调用成功于设置默认快捷键，**则为 true** 。 否则为 **false**。

## <a name="set_default_cpu_access_type"></a>set_default_cpu_access_type

设置在此快捷键上创建的数组的默认 cpu access_type，或设置为在此加速器上访问 array_views 的一部分的隐式内存分配。 此方法仅在以下情况下才会成功：快捷键的 default_cpu_access_type 尚未由先前对此方法的调用重写，并且此快捷键的所选 default_cpu_access_type 尚未用于分配数组或支持在此加速器上访问 array_view 的隐式内存分配。

```cpp
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```

### <a name="parameters"></a>parameters

*_Default_cpu_access_type*<br/>
要用于此加速器上的 array/array_view 内存分配的默认 cpu access_type。

### <a name="return-value"></a>返回值

一个布尔值，指示是否已成功设置快捷键的默认 cpu access_type。

## <a name="supports_cpu_shared_memory"></a>supports_cpu_shared_memory

获取一个布尔值，该值指示 `accelerator` 是否支持共享内存。

```cpp
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;
```

## <a name="supports_double_precision"></a>supports_double_precision

获取一个指示快捷键是否支持双精度算术的布尔值。

```cpp
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;
```

## <a name="supports_limited_double_precision"></a>supports_limited_double_precision

获取一个布尔值，该值指示快捷键是否对双精度算术的支持有限。 如果快捷键仅提供有限的支持，则不支持融化乘法加法 (FMA)、除法以及 `int` 和 `double` 之间的相互转换。

```cpp
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;
```

## <a name="version"></a>版本

获取 `accelerator` 的版本。

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="see-also"></a>另请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)

---
title: accelerator 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- accelerator class
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b40177af3796a17d32e78e628c41ea694f69ed9f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694746"
---
# <a name="accelerator-class"></a>accelerator 类
加速器是针对数据并行计算进行了优化的硬件功能。 加速器可能是设备连接到 PCIe 总线 （如 GPU)，也可能是在主要的 CPU 上设置的扩展的指令。  
  
## <a name="syntax"></a>语法  
  
```  
class accelerator;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[accelerator 构造函数](#ctor)|初始化 `accelerator` 类的新实例。|  
|[~ accelerator 析构函数](#ctor)|销毁`accelerator`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[create_view](#create_view)|创建并返回`accelerator_view`在此快捷键上的对象。|  
|[get_all](#get_all)|返回向量的`accelerator`表示所有可用的快捷键的对象。|  
|[get_auto_selection_view](#get_auto_selection_view)|返回自动选择`accelerator_view`。|  
|[get_dedicated_memory](#get_dedicated_memory)|返回的专用的内存`accelerator`，以千字节为单位。|  
|[get_default_cpu_access_type](#get_default_cpu_access_type)|返回默认值[access_type](concurrency-namespace-enums-amp.md#access_type)在此快捷键上创建的缓冲区。|  
|[get_default_view](#get_default_view)|返回默认值`accelerator_view`与关联的对象`accelerator`。|  
|[get_description](#get_description)|返回的简短说明`accelerator`设备。|  
|[get_device_path](#get_device_path)|返回设备的路径。|  
|[get_has_display](#get_has_display)|确定是否`accelerator`附加到的显示器。|  
|[get_is_debug](#get_is_debug)|确定是否`accelerator`为广泛的错误报告启用了调试层。|  
|[get_is_emulated](#get_is_emulated)|确定是否`accelerator`被模拟。|  
|[get_supports_cpu_shared_memory](#get_supports_cpu_shared_memory)|确定是否`accelerator`支持共享内存|  
|[get_supports_double_precision](#get_supports_double_precision)|确定是否`accelerator`附加到的显示器。|  
|[get_supports_limited_double_precision](#get_supports_limited_double_precision)|确定是否`accelerator`提供有限的双精度算术的支持。|  
|[get_version](#get_version)|返回的版本`accelerator`。|  
|[set_default](#set_default)|返回的默认快捷键的路径。|  
|[set_default_cpu_access_type](#set_default_cpu_access_type)|设置默认 CPU [access_type](concurrency-namespace-enums-amp.md#access_type)数组和对此进行隐式的内存分配`accelerator`。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[operator!=](#operator_neq)|比较此`accelerator`与另一个对象，并返回`false`如果它们是相同的; 否则，返回`true`。|  
|[operator=](#operator_eq)|将指定的内容复制`accelerator`于此对象。|  
|[operator==](#operator_eq_eq)|比较此`accelerator`与另一个对象，并返回`true`如果它们是相同的; 否则，返回`false`。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[cpu_accelerator](#cpu_accelerator)|获取一个字符串常数 CPU `accelerator`。|  
|[dedicated_memory](#dedicated_memory)|获取专用的内存`accelerator`，以千字节为单位。|  
|[default_accelerator](#default_accelerator)|获取默认值的字符串常量`accelerator`。|  
|[default_cpu_access_type](#default_cpu_access_type)|获取或设置默认 CPU [access_type](concurrency-namespace-enums-amp.md#access_type)数组和对此进行隐式的内存分配`accelerator`。|  
|[default_view](#default_view)|获取默认`accelerator_view`与关联的对象`accelerator`。|  
|[description](#description)|获取的简短说明`accelerator`设备。|  
|[device_path](#device_path)|获取设备的路径。|  
|[direct3d_ref](#direct3d_ref)|获取 Direct3D 引用的字符串常量`accelerator`。|  
|[direct3d_warp](#direct3d_warp)|获取的字符串常数`accelerator`对象，你可将用于在使用流式处理 SIMD 扩展 (SSE) 的多核 Cpu 上执行 c + + AMP 代码。|  
|[has_display](#has_display)|获取一个布尔值，该值指示是否`accelerator`附加到的显示器。|  
|[is_debug](#is_debug)|指示是否`accelerator`为广泛的错误报告启用了调试层。|  
|[is_emulated](#is_emulated)|指示是否`accelerator`被模拟。|  
|[supports_cpu_shared_memory](#supports_cpu_shared_memory)|指示是否`accelerator`支持共享内存。|  
|[supports_double_precision](#supports_double_precision)|指示快捷键是否支持双精度算术。|  
|[supports_limited_double_precision](#supports_limited_double_precision)|指示快捷键是否提供有限的双精度算术的支持。|  
|[version](#version)|获取的版本`accelerator`。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `accelerator`  
  
## <a name="remarks"></a>备注  
 加速器是针对数据并行计算进行了优化的硬件功能。 加速器通常离散 GPU，但它也可以是虚拟的主机端实体，如 DirectX REF 设备，一种变形 （的 CPU 端设备加速通过 SSE 指令） 或 CPU 本身。  
  
 您可以构造`accelerator`对象通过枚举可用的设备，或获取默认设备、 引用设备或 WARP 设备。  
  
## <a name="requirements"></a>要求  
 **标头：** amprt.h  
  
 **命名空间：** 并发  
  
##  <a name="dtor"></a> </a> ~ 快捷键 

 销毁`accelerator`对象。  
  
```  
~accelerator();
```  
  
### <a name="return-value"></a>返回值  
  
##  <a name="ctor"></a> 快捷键 

 初始化的新实例[accelerator 类](accelerator-class.md)。  
  
```  
accelerator();

 
explicit accelerator(const std::wstring& _Device_path);

 
accelerator(const accelerator& _Other);
```  
  
### <a name="parameters"></a>参数  
 `_Device_path`  
 物理设备的路径。  
  
 `_Other`  
 要复制的快捷键。  
  
##  <a name="cpu_accelerator"></a> cpu_accelerator 

 获取 CPU 快捷键的字符串常数。  
  
```  
static const wchar_t cpu_accelerator[];  
```  
  
##  <a name="create_view"></a> create_view 

 使用指定的排队模式，在快捷键上创建并返回一个 `accelerator_view` 对象。 未指定排队模式时，新`accelerator_view`使用[queuing_mode:: immediate](concurrency-namespace-enums-amp.md#queuing_mode)排队模式。  
  
```  
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```  
  
### <a name="parameters"></a>参数  
 `qmode`  
 排队模式。  
  
### <a name="return-value"></a>返回值  
 使用指定队列的模式，在此快捷键上创建的新 `accelerator_view` 对象。  
  
##  <a name="dedicated_memory"></a> dedicated_memory 

 获取专用的内存`accelerator`，以千字节为单位。  
  
```  
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;  
```  
  
##  <a name="default_accelerator"></a> default_accelerator 

 获取默认值的字符串常量`accelerator`。  
  
```  
static const wchar_t default_accelerator[];  
```  
  
##  <a name="default_cpu_access_type"></a> default_cpu_access_type 

 默认值 cpu [access_type](concurrency-namespace-enums-amp.md#access_type)数组和隐式的内存分配对此这`accelerator`。  
  
```  
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;  
```  
  
##  <a name="default_view"></a> default_view 

 获取与关联的默认快捷键视图`accelerator`。  
  
```  
__declspec(property(get= get_default_view)) accelerator_view default_view;  
```  
  
##  <a name="description"></a> 说明 

 获取的简短说明`accelerator`设备。  
  
```  
__declspec(property(get= get_description)) std::wstring description;  
```  
  
##  <a name="device_path"></a> device_path 

 获取快捷键的路径。 该路径在系统上是唯一的。  
  
```  
__declspec(property(get= get_device_path)) std::wstring device_path;  
```  
  
##  <a name="direct3d_ref"></a> direct3d_ref 

 获取 Direct3D 引用快捷键的字符串常数。  
  
```  
static const wchar_t direct3d_ref[];  
```  
  
##  <a name="direct3d_warp"></a> direct3d_warp 

 获取的字符串常数`accelerator`对象，你可将用于在使用流式处理 SIMD 扩展 (SSE) 的多核 Cpu 上执行 c + + AMP 代码。  
  
```  
static const wchar_t direct3d_warp[];  
```  
  
##  <a name="get_all"></a> get_all 

 返回向量的`accelerator`表示所有可用的快捷键的对象。  
  
```  
static inline std::vector<accelerator> get_all();
```  
  
### <a name="return-value"></a>返回值  
 可用快捷键的矢量  
  
##  <a name="get_auto_selection_view"></a> get_auto_selection_view 

 返回自动选择 accelerator_view，当指定为用于执行要由运行时自动选择的 parallel_for_each 内核目标 accelerator_view 中的 parallel_for_each 目标结果。 对于所有其他而言，此方法返回 accelerator_view 是默认快捷键默认 accelerator_view 相同  
  
```  
static accelerator_view __cdecl get_auto_selection_view();
```  
  
### <a name="return-value"></a>返回值  
 自动选择 accelerator_view。  
  
##  <a name="get_dedicated_memory"></a> get_dedicated_memory 

 返回的专用的内存`accelerator`，以千字节为单位。  
  
```  
size_t get_dedicated_memory() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `accelerator` 的专用内存（单位为 KB）。  
  
##  <a name="get_default_cpu_access_type"></a> get_default_cpu_access_type 

 获取在此快捷键上创建的缓冲区的默认 cpu access_type  
  
```  
access_type get_default_cpu_access_type() const;

 
```  
  
### <a name="return-value"></a>返回值  
 在此快捷键上创建的缓冲区默认 cpu access_type。  
  
##  <a name="get_default_view"></a> get_default_view 

 返回默认值`accelerator_view`与关联的对象`accelerator`。  
  
```  
accelerator_view get_default_view() const;

 
```  
  
### <a name="return-value"></a>返回值  
 与 `accelerator_view` 关联的默认 `accelerator` 对象。  
  
##  <a name="get_description"></a> get_description 

 返回的简短说明`accelerator`设备。  
  
```  
std::wstring get_description() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `accelerator` 设备的简短说明。  
  
##  <a name="get_device_path"></a> get_device_path 

 返回的快捷键的路径。 该路径在系统上是唯一的。  
  
```  
std::wstring get_device_path() const;

 
```  
  
### <a name="return-value"></a>返回值  
 系统范围内唯一的设备实例路径。  
  
##  <a name="get_has_display"></a> get_has_display 

 返回一个布尔值，该值指示是否`accelerator`可以输出到的显示器。  
  
```  
bool get_has_display() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果`accelerator`可以输出为显示; 否则为`false`。  
  
##  <a name="get_is_debug"></a> get_is_debug 

 确定是否`accelerator`为广泛的错误报告启用了调试层。  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果`accelerator`为广泛的错误报告启用了调试层。 否则为 `false`。  
  
##  <a name="get_is_emulated"></a> get_is_emulated 

 确定是否`accelerator`被模拟。  
  
```  
bool get_is_emulated() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果`accelerator`被模拟。 否则为 `false`。  
  
##  <a name="get_supports_cpu_shared_memory"></a> get_supports_cpu_shared_memory 

 返回一个布尔值，该值指示快捷键是否支持快捷键和 CPU 可访问的内存。  
  
```  
bool get_supports_cpu_shared_memory() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果快捷键支持共享的 CPU 内存;否则为`false`。  
  
##  <a name="get_supports_double_precision"></a> get_supports_double_precision 

 返回一个布尔值，该值指示是否快捷键支持双精度算术，包括融化乘法加法 (FMA)、 除法以及相互之间的强制转换`int`和`double`。  
  
```  
bool get_supports_double_precision() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果快捷键支持双精度算术;否则为`false`。  
  
##  <a name="get_supports_limited_double_precision"></a> get_supports_limited_double_precision 

 返回一个布尔值，指示快捷键是否限制了对双精度算术的支持。 如果快捷键仅提供有限的支持，则不支持融化乘法加法 (FMA)、除法以及 `int` 和 `double` 之间的相互转换。  
  
```  
bool get_supports_limited_double_precision() const;

 
```  
  
### <a name="return-value"></a>返回值  
 如果快捷键对双精度算术只提供有限的支持，则为 `true`；否则为 `false`。  
  
##  <a name="get_version"></a> get_version 

 返回的版本`accelerator`。  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>返回值  
 版本`accelerator`。  
  
##  <a name="has_display"></a> has_display 

 获取一个布尔值，该值指示是否`accelerator`可以输出到的显示器。  
  
```  
__declspec(property(get= get_has_display)) bool has_display;  
```  
  
##  <a name="is_debug"></a> is_debug 

 获取一个布尔值，该值指示是否`accelerator`为广泛的错误报告启用了调试层。  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="is_emulated"></a> is_emulated 

 获取一个布尔值，该值指示是否`accelerator`被模拟。  
  
```  
__declspec(property(get= get_is_emulated)) bool is_emulated;  
```  
  
##  <a name="operator_neq"></a> 运算符 ！ = 

 比较此`accelerator`与另一个对象，并返回`false`如果它们是相同的; 否则，返回`true`。  
  
```  
bool operator!= (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 与此对象相比较的 `accelerator` 对象。  
  
### <a name="return-value"></a>返回值  
 `false` 如果两个`accelerator`对象是否相同; 否则为`true`。  
  
##  <a name="operator_eq"></a> 运算符 = 

 将指定的内容复制`accelerator`于此对象。  
  
```  
accelerator& operator= (const accelerator& _Other);
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `accelerator`从中进行复制的对象。  
  
### <a name="return-value"></a>返回值  
 对此引用`accelerator`对象。  
  
##  <a name="operator_eq_eq"></a> 运算符 = = 

 比较此`accelerator`与另一个对象，并返回`true`如果它们是相同的; 否则，返回`false`。  
  
```  
bool operator== (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 与此对象相比较的 `accelerator` 对象。  
  
### <a name="return-value"></a>返回值  
 `true` 如果其他`accelerator`对象是与此相同`accelerator`对象; 否则为`false`。  
  
##  <a name="set_default"></a> set_default 

 设置要用于任何隐式使用默认快捷键操作的默认快捷键。 如果运行时所选的默认快捷键不已使用隐式使用默认快捷键操作中，此方法才会成功  
  
```  
static inline bool set_default(std::wstring _Path);
```  
  
### <a name="parameters"></a>参数  
 `_Path`  
 指向快捷键的路径。  
  
### <a name="return-value"></a>返回值  
 `true` 如果调用成功在设置默认快捷键。 否则为 `false`。  
  
##  <a name="set_default_cpu_access_type"></a> set_default_cpu_access_type 

 设置默认 cpu access_type 数组创建在此快捷键上或隐式的内存分配，因为此快捷键上访问 array_views 的一部分。 如果快捷键 default_cpu_access_type 尚未被重写此方法的以前调用和用于分配一个数组或具有不已用于此快捷键运行时选择 default_cpu_access_type，此方法才会成功备份在此快捷键上访问 array_view 执行隐式的内存分配。  
  
```  
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```  
  
### <a name="parameters"></a>参数  
 `_Default_cpu_access_type`  
 要用于在此快捷键上数组/array_view 内存分配默认 cpu access_type。  
  
### <a name="return-value"></a>返回值  
 一个布尔值，该值指示是否已成功将快捷键默认 cpu access_type 的设置。  
  
##  <a name="supports_cpu_shared_memory"></a> supports_cpu_shared_memory 

 获取一个布尔值，该值指示是否`accelerator`支持共享内存。  
  
```  
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;  
```  
  
##  <a name="supports_double_precision"></a> supports_double_precision 

 获取一个指示快捷键是否支持双精度算术的布尔值。  
  
```  
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;  
```  
  
##  <a name="supports_limited_double_precision"></a> supports_limited_double_precision 

 获取一个布尔值，该值指示快捷键是否提供有限的双精度算术的支持。 如果快捷键仅提供有限的支持，则不支持融化乘法加法 (FMA)、除法以及 `int` 和 `double` 之间的相互转换。  
  
```  
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;  
```  
  
##  <a name="version"></a> 版本 

 获取的版本`accelerator`。  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="dtor"></a> </a> ~ accelerator_view 

 销毁[accelerator_view](accelerator-view-class.md)对象。  
  
```  
~accelerator_view();
```  
  
### <a name="return-value"></a>返回值  
  
##  <a name="accelerator"></a> 快捷键 

 获取`accelerator`对象[accelerator_view](accelerator-view-class.md)对象。  
  
```  
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;  
```  
  
##  <a name="ctor"></a> accelerator_view 

 初始化的新实例[accelerator_view](accelerator-view-class.md)通过复制现有的类`accelerator_view`对象。  
  
```  
accelerator_view(const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `accelerator_view`要复制的对象。  
  
##  <a name="create_marker"></a> create_marker 

 返回将来要跟踪的所有命令提交到目前为止至此完成`accelerator_view`对象。  
  
```  
concurrency::completion_future create_marker();
```  
  
### <a name="return-value"></a>返回值  
 将来要跟踪的所有命令提交到目前为止至此完成`accelerator_view`对象。  
  
##  <a name="flush"></a> 刷新 

 提交所有挂起命令排队到[accelerator_view](accelerator-view-class.md)给快捷键执行的对象。  
  
```  
void flush();
```  
  
### <a name="return-value"></a>返回值  
 返回 `void`。  
  
##  <a name="get_accelerator"></a> get_accelerator 

 返回`accelerator`对象[accelerator_view](accelerator-view-class.md)对象。  
  
```  
accelerator get_accelerator() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `accelerator`对象`accelerator_view`对象。  
  
##  <a name="get_is_auto_selection"></a> get_is_auto_selection 

 返回一个布尔值，该值指示是否 accelerator_view 传递给时，运行时将自动选择相应加速器[parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each)。  
  
```  
bool get_is_auto_selection() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果运行时将自动选择相应加速器;否则为`false`。  
  
##  <a name="get_is_debug"></a> get_is_debug 

 返回一个布尔值，该值指示是否[accelerator_view](accelerator-view-class.md)对象具有为广泛的错误报告启用了调试层。  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>返回值  
 一个布尔值，指示 `accelerator_view` 对象是否为广泛的错误报告启用了调试层。  
  
##  <a name="get_queuing_mode"></a> get_queuing_mode 

 返回的排队模式[accelerator_view](accelerator-view-class.md)对象。  
  
```  
queuing_mode get_queuing_mode() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `accelerator_view` 对象的排队模式。  
  
##  <a name="get_version"></a> get_version 

 返回的版本[accelerator_view](accelerator-view-class.md)。  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>返回值  
 版本`accelerator_view`。  
  
##  <a name="is_auto_selection"></a> is_auto_selection 

 获取一个布尔值，该值指示是否 accelerator_view 传递给时，运行时将自动选择相应加速器[parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each)。  
  
```  
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;  
```  
  
##  <a name="is_debug"></a> is_debug 

 获取一个布尔值，该值指示是否[accelerator_view](accelerator-view-class.md)对象具有为广泛的错误报告启用了调试层。  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="operator_neq"></a> 运算符 ！ = 

 比较此[accelerator_view](accelerator-view-class.md)与另一个对象，并返回`false`如果它们是相同的; 否则，返回`true`。  
  
```  
bool operator!= (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 与此对象相比较的 `accelerator_view` 对象。  
  
### <a name="return-value"></a>返回值  
 如果两个对象相同，则为 `false`；否则为 `true`。  
  
##  <a name="operator_eq"></a> 运算符 = 

 将指定的内容复制[accelerator_view](accelerator-view-class.md)到此对象。  
  
```  
accelerator_view& operator= (const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `accelerator_view`从中进行复制的对象。  
  
### <a name="return-value"></a>返回值  
 对修改后的 `accelerator_view` 对象的引用。  
  
##  <a name="operator_eq_eq"></a> 运算符 = = 

 比较此[accelerator_view](accelerator-view-class.md)与另一个对象，并返回`true`如果它们是相同的; 否则，返回`false`。  
  
```  
bool operator== (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 与此对象相比较的 `accelerator_view` 对象。  
  
### <a name="return-value"></a>返回值  
 如果两个对象相同，则为 `true`；否则为 `false`。  
  
##  <a name="queuing_mode"></a> queuing_mode 

 获取的排队模式[accelerator_view](accelerator-view-class.md)对象。  
  
```  
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;  
```  
  
##  <a name="version"></a> 版本 

 获取的版本[accelerator_view](accelerator-view-class.md)。  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="wait"></a> 等待 

 等待提交到的所有命令[accelerator_view](accelerator-view-class.md)对象来完成。  
  
```  
void wait();
```  
  
### <a name="return-value"></a>返回值  
 返回 `void`。  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)

---
title: "accelerator 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amprt/Concurrency::accelerator
dev_langs:
- C++
helpviewer_keywords:
- accelerator class
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
caps.latest.revision: 29
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: b1bdd7f6979094658d1de6f9690bc44dc50ee8bb
ms.lasthandoff: 02/24/2017

---
# <a name="accelerator-class"></a>accelerator 类
加速器是针对数据并行计算进行了优化的硬件功能。 加速器可能是设备连接到 PCIe 总线 （如 GPU)，或者它可能在主 CPU 上设置的扩展的指令。  
  
## <a name="syntax"></a>语法  
  
```  
class accelerator;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[accelerator 构造函数](#ctor)|初始化 `accelerator` 类的新实例。|  
|[~ accelerator 析构函数](#ctor)|销毁`accelerator`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[create_view 方法](#create_view)|创建并返回`accelerator_view`在此快捷键上的对象。|  
|[get_all 方法](#get_all)|返回一个向量`accelerator`这些对象表示所有可用的快捷键。|  
|[get_auto_selection_view 方法](#get_auto_selection_view)|返回自动选取`accelerator_view`。|  
|[get_dedicated_memory 方法](#get_dedicated_memory)|返回的专用的内存`accelerator`，以千字节为单位。|  
|[get_default_cpu_access_type 方法](#get_default_cpu_access_type)|返回的默认[access_type](concurrency-namespace-enums-amp.md#access_type)为在此快捷键上创建的缓冲区。|  
|[get_default_view 方法](#get_default_view)|返回的默认`accelerator_view`与关联的对象`accelerator`。|  
|[get_description 方法](#get_description)|返回的简短说明`accelerator`设备。|  
|[get_device_path 方法](#get_device_path)|返回该设备的路径。|  
|[get_has_display 方法](#get_has_display)|确定是否`accelerator`附加到一个显示器。|  
|[get_is_debug 方法](#get_is_debug)|确定是否`accelerator`为广泛的错误报告启用了调试层。|  
|[get_is_emulated 方法](#get_is_emulated)|确定是否`accelerator`被模拟。|  
|[get_supports_cpu_shared_memory 方法](#get_supports_cpu_shared_memory)|确定是否`accelerator`支持共享内存|  
|[get_supports_double_precision 方法](#get_supports_double_precision)|确定是否`accelerator`附加到一个显示器。|  
|[get_supports_limited_double_precision 方法](#get_supports_limited_double_precision)|确定是否`accelerator`提供有限的双精度算术的支持。|  
|[get_version 方法](#get_version)|返回的版本`accelerator`。|  
|[set_default 方法](#set_default)|返回默认快捷键的路径。|  
|[set_default_cpu_access_type 方法](#set_default_cpu_access_type)|设置默认 CPU [access_type](concurrency-namespace-enums-amp.md#access_type)数组和对此进行隐式的内存分配`accelerator`。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[运算符 ！ = 运算符](#operator_neq)|比较此`accelerator`与另一个对象，并返回`false`如果它们是相同的; 否则，返回`true`。|  
|[运算符 = 运算符](#operator_eq)|将指定的内容复制`accelerator`对象传递给它。|  
|[运算符 = = 运算符](#operator_eq_eq)|比较此`accelerator`与另一个对象，并返回`true`如果它们是相同的; 否则，返回`false`。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[cpu_accelerator 数据成员](#cpu_accelerator)|获取一个字符串常数 CPU `accelerator`。|  
|[dedicated_memory 数据成员](#dedicated_memory)|获取专用的内存`accelerator`，以千字节为单位。|  
|[default_accelerator 数据成员](#default_accelerator)|获取一个字符串常量默认`accelerator`。|  
|[default_cpu_access_type 数据成员](#default_cpu_access_type)|获取或设置默认 CPU [access_type](concurrency-namespace-enums-amp.md#access_type)数组和对此进行隐式的内存分配`accelerator`。|  
|[default_view 数据成员](#default_view)|获取默认`accelerator_view`与关联的对象`accelerator`。|  
|[说明数据成员](#description)|获取的简短说明`accelerator`设备。|  
|[device_path 数据成员](#device_path)|获取设备的路径。|  
|[direct3d_ref 数据成员](#direct3d_ref)|获取 Direct3D 引用的字符串常量`accelerator`。|  
|[direct3d_warp 数据成员](#direct3d_warp)|获取的字符串常量，`accelerator`对象，您可将用于在使用流式处理 SIMD 扩展 (SSE) 的多核 Cpu 上执行 c + + AMP 代码。|  
|[has_display 数据成员](#has_display)|获取一个布尔值，该值指示是否`accelerator`附加到一个显示器。|  
|[is_debug 数据成员](#is_debug)|指示是否`accelerator`为广泛的错误报告启用了调试层。|  
|[is_emulated 数据成员](#is_emulated)|指示是否`accelerator`被模拟。|  
|[supports_cpu_shared_memory 数据成员](#supports_cpu_shared_memory)|指示是否`accelerator`支持共享内存。|  
|[supports_double_precision 数据成员](#supports_double_precision)|指示快捷键是否支持双精度算术。|  
|[supports_limited_double_precision 数据成员](#supports_limited_double_precision)|指示快捷键是否限制了对双精度算术的支持。|  
|[版本的数据成员](#version)|获取的版本`accelerator`。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `accelerator`  
  
## <a name="remarks"></a>备注  
 加速器是针对数据并行计算进行了优化的硬件功能。 加速器通常是离散的 GPU，但它也可以是虚拟的宿主端实体，如一种变形 （的 CPU 端设备通过 SSE 指令加速） 或 CPU 自身的 DirectX REF 设备。  
  
 您可以构造`accelerator`通过枚举可用的设备，或通过获取默认的设备、 引用设备或 WARP 设备对象。  
  
## <a name="requirements"></a>要求  
 **标头︰** amprt.h  
  
 **命名空间：** 并发  
  
##  <a name="dtor"></a></a> ~ 加速器 

 销毁`accelerator`对象。  
  
```  
~accelerator();
```  
  
### <a name="return-value"></a>返回值  
  
##  <a name="a-namectora-accelerator"></a><a name="ctor"></a>加速器 

 新实例初始化[accelerator 类](accelerator-class.md)。  
  
```  
accelerator();

 
explicit accelerator(const std::wstring& _Device_path);

 
accelerator(const accelerator& _Other);
```  
  
### <a name="parameters"></a>参数  
 `_Device_path`  
 物理设备的路径。  
  
 `_Other`  
 若要复制的快捷键。  
  
##  <a name="a-namecpuacceleratora-cpuaccelerator"></a><a name="cpu_accelerator"></a>cpu_accelerator 

 获取 CPU 快捷键的字符串常数。  
  
```  
static const wchar_t cpu_accelerator[];  
```  
  
##  <a name="a-namecreateviewa-createview"></a><a name="create_view"></a>create_view 

 使用指定的排队模式，在快捷键上创建并返回一个 `accelerator_view` 对象。 如果未指定排队模式，新`accelerator_view`使用[queuing_mode:: immediate](concurrency-namespace-enums-amp.md#queuing_mode)排队模式。  
  
```  
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```  
  
### <a name="parameters"></a>参数  
 `qmode`  
 排队模式。  
  
### <a name="return-value"></a>返回值  
 使用指定队列的模式，在此快捷键上创建的新 `accelerator_view` 对象。  
  
##  <a name="a-namededicatedmemorya-dedicatedmemory"></a><a name="dedicated_memory"></a>dedicated_memory 

 获取专用的内存`accelerator`，以千字节为单位。  
  
```  
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;  
```  
  
##  <a name="a-namedefaultacceleratora-defaultaccelerator"></a><a name="default_accelerator"></a>default_accelerator 

 获取一个字符串常量默认`accelerator`。  
  
```  
static const wchar_t default_accelerator[];  
```  
  
##  <a name="a-namedefaultcpuaccesstypea-defaultcpuaccesstype"></a><a name="default_cpu_access_type"></a>default_cpu_access_type 

 默认值 cpu [access_type](concurrency-namespace-enums-amp.md#access_type)数组和此内容进行隐式的内存分配`accelerator`。  
  
```  
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;  
```  
  
##  <a name="a-namedefaultviewa-defaultview"></a><a name="default_view"></a>default_view 

 获取与之关联的默认快捷键视图`accelerator`。  
  
```  
__declspec(property(get= get_default_view)) accelerator_view default_view;  
```  
  
##  <a name="a-namedescriptiona-description"></a><a name="description"></a>说明 

 获取的简短说明`accelerator`设备。  
  
```  
__declspec(property(get= get_description)) std::wstring description;  
```  
  
##  <a name="a-namedevicepatha-devicepath"></a><a name="device_path"></a>device_path 

 获取快捷键的路径。 该路径在系统上是唯一的。  
  
```  
__declspec(property(get= get_device_path)) std::wstring device_path;  
```  
  
##  <a name="a-namedirect3drefa-direct3dref"></a><a name="direct3d_ref"></a>direct3d_ref 

 获取 Direct3D 引用快捷键的字符串常数。  
  
```  
static const wchar_t direct3d_ref[];  
```  
  
##  <a name="a-namedirect3dwarpa-direct3dwarp"></a><a name="direct3d_warp"></a>direct3d_warp 

 获取的字符串常量，`accelerator`对象，您可将用于使用流式处理 SIMD 扩展 (SSE) 的多核 Cpu 上执行 c + + AMP 代码。  
  
```  
static const wchar_t direct3d_warp[];  
```  
  
##  <a name="a-namegetalla-getall"></a><a name="get_all"></a>get_all 

 返回一个向量`accelerator`这些对象表示所有可用的快捷键。  
  
```  
static inline std::vector<accelerator> get_all();
```  
  
### <a name="return-value"></a>返回值  
 可用快捷键的矢量  
  
##  <a name="a-namegetautoselectionviewa-getautoselectionview"></a><a name="get_auto_selection_view"></a>get_auto_selection_view 

 返回自动选择 accelerator_view，当指定为用于执行要由运行时自动选择的 parallel_for_each 内核目标 accelerator_view parallel_for_each 目标结果。 用于其他目的，此方法返回 accelerator_view 等同于默认快捷键默认 accelerator_view  
  
```  
static accelerator_view __cdecl get_auto_selection_view();
```  
  
### <a name="return-value"></a>返回值  
 自动选择 accelerator_view。  
  
##  <a name="a-namegetdedicatedmemorya-getdedicatedmemory"></a><a name="get_dedicated_memory"></a>get_dedicated_memory 

 返回的专用的内存`accelerator`，以千字节为单位。  
  
```  
size_t get_dedicated_memory() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `accelerator` 的专用内存（单位为 KB）。  
  
##  <a name="a-namegetdefaultcpuaccesstypea-getdefaultcpuaccesstype"></a><a name="get_default_cpu_access_type"></a>get_default_cpu_access_type 

 获取在此快捷键上创建的缓冲区的默认 cpu access_type  
  
```  
access_type get_default_cpu_access_type() const;

 
```  
  
### <a name="return-value"></a>返回值  
 在此快捷键上创建的缓冲区默认 cpu access_type。  
  
##  <a name="a-namegetdefaultviewa-getdefaultview"></a><a name="get_default_view"></a>get_default_view 

 返回的默认`accelerator_view`与关联的对象`accelerator`。  
  
```  
accelerator_view get_default_view() const;

 
```  
  
### <a name="return-value"></a>返回值  
 与 `accelerator_view` 关联的默认 `accelerator` 对象。  
  
##  <a name="a-namegetdescriptiona-getdescription"></a><a name="get_description"></a>get_description 

 返回的简短说明`accelerator`设备。  
  
```  
std::wstring get_description() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `accelerator` 设备的简短说明。  
  
##  <a name="a-namegetdevicepatha-getdevicepath"></a><a name="get_device_path"></a>get_device_path 

 返回快捷键的路径。 该路径在系统上是唯一的。  
  
```  
std::wstring get_device_path() const;

 
```  
  
### <a name="return-value"></a>返回值  
 系统范围内唯一的设备实例路径。  
  
##  <a name="a-namegethasdisplaya-gethasdisplay"></a><a name="get_has_display"></a>get_has_display 

 返回一个布尔值，该值指示是否`accelerator`可以输出到显示器。  
  
```  
bool get_has_display() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true`如果`accelerator`可以输出到显示器; 否则为`false`。  
  
##  <a name="a-namegetisdebuga-getisdebug"></a><a name="get_is_debug"></a>get_is_debug 

 确定是否`accelerator`为广泛的错误报告启用了调试层。  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true`如果`accelerator`为广泛的错误报告启用了调试层。 否则为 `false`。  
  
##  <a name="a-namegetisemulateda-getisemulated"></a><a name="get_is_emulated"></a>get_is_emulated 

 确定是否`accelerator`被模拟。  
  
```  
bool get_is_emulated() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true`如果`accelerator`被模拟。 否则为 `false`。  
  
##  <a name="a-namegetsupportscpusharedmemorya-getsupportscpusharedmemory"></a><a name="get_supports_cpu_shared_memory"></a>get_supports_cpu_shared_memory 

 返回一个布尔值，该值指示快捷键是否支持内存都可访问，同时通过加速器和 CPU。  
  
```  
bool get_supports_cpu_shared_memory() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true`如果快捷键支持 CPU 共享内存;否则为`false`。  
  
##  <a name="a-namegetsupportsdoubleprecisiona-getsupportsdoubleprecision"></a><a name="get_supports_double_precision"></a>get_supports_double_precision 

 返回一个布尔值，该值指示是否加速器支持双精度算术，包括融化乘法加法 (FMA)、 除法以及相互之间的强制转换`int`和`double`。  
  
```  
bool get_supports_double_precision() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true`如果快捷键支持双精度算术;否则为`false`。  
  
##  <a name="a-namegetsupportslimiteddoubleprecisiona-getsupportslimiteddoubleprecision"></a><a name="get_supports_limited_double_precision"></a>get_supports_limited_double_precision 

 返回一个布尔值，指示快捷键是否限制了对双精度算术的支持。 如果快捷键仅提供有限的支持，则不支持融化乘法加法 (FMA)、除法以及 `int` 和 `double` 之间的相互转换。  
  
```  
bool get_supports_limited_double_precision() const;

 
```  
  
### <a name="return-value"></a>返回值  
 如果快捷键对双精度算术只提供有限的支持，则为 `true`；否则为 `false`。  
  
##  <a name="a-namegetversiona-getversion"></a><a name="get_version"></a>get_version 

 返回的版本`accelerator`。  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>返回值  
 版本`accelerator`。  
  
##  <a name="a-namehasdisplaya-hasdisplay"></a><a name="has_display"></a>has_display 

 获取一个布尔值，该值指示是否`accelerator`可以输出到显示器。  
  
```  
__declspec(property(get= get_has_display)) bool has_display;  
```  
  
##  <a name="a-nameisdebuga-isdebug"></a><a name="is_debug"></a>is_debug 

 获取一个布尔值，该值指示是否`accelerator`为广泛的错误报告启用了调试层。  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="a-nameisemulateda-isemulated"></a><a name="is_emulated"></a>is_emulated 

 获取一个布尔值，该值指示是否`accelerator`被模拟。  
  
```  
__declspec(property(get= get_is_emulated)) bool is_emulated;  
```  
  
##  <a name="a-nameoperatorneqa-operator"></a><a name="operator_neq"></a>运算符 ！ = 

 比较此`accelerator`与另一个对象，并返回`false`如果它们是相同的; 否则，返回`true`。  
  
```  
bool operator!= (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 与此对象相比较的 `accelerator` 对象。  
  
### <a name="return-value"></a>返回值  
 `false`如果两个`accelerator`对象是否相同; 否则为`true`。  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>运算符 = 

 将指定的内容复制`accelerator`对象传递给它。  
  
```  
accelerator& operator= (const accelerator& _Other);
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `accelerator`从其中复制对象。  
  
### <a name="return-value"></a>返回值  
 参考这`accelerator`对象。  
  
##  <a name="a-nameoperatoreqeqa-operator"></a><a name="operator_eq_eq"></a>运算符 = = 

 比较此`accelerator`与另一个对象，并返回`true`如果它们是相同的; 否则，返回`false`。  
  
```  
bool operator== (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 与此对象相比较的 `accelerator` 对象。  
  
### <a name="return-value"></a>返回值  
 `true`如果其他`accelerator`对象是与此相同`accelerator`对象; 否则为`false`。  
  
##  <a name="a-namesetdefaulta-setdefault"></a><a name="set_default"></a>set_default 

 设置默认快捷键用于隐式地使用默认快捷键的任何操作。 此方法才会成功运行时所选的默认快捷键具有已中尚未使用隐式使用默认快捷键的操作  
  
```  
static inline bool set_default(std::wstring _Path);
```  
  
### <a name="parameters"></a>参数  
 `_Path`  
 指向快捷键的路径。  
  
### <a name="return-value"></a>返回值  
 `true`如果调用成功保持设置默认快捷键。 否则为 `false`。  
  
##  <a name="a-namesetdefaultcpuaccesstypea-setdefaultcpuaccesstype"></a><a name="set_default_cpu_access_type"></a>set_default_cpu_access_type 

 设置默认 cpu access_type array_views 的一部分对此此加速器访问创建在此快捷键上或用于隐式的内存分配的数组。 此方法才会成功。 如果加速器 default_cpu_access_type 尚未被重写此方法的以前调用，并且分配了数组或备份在此快捷键上访问 array_view 执行隐式的内存分配以前未被使用此加速器所选的运行时 default_cpu_access_type。  
  
```  
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```  
  
### <a name="parameters"></a>参数  
 `_Default_cpu_access_type`  
 要用于在此快捷键上数组/array_view 内存分配默认 cpu access_type。  
  
### <a name="return-value"></a>返回值  
 一个布尔值，该值指示快捷键默认 cpu access_type 已成功设置。  
  
##  <a name="a-namesupportscpusharedmemorya-supportscpusharedmemory"></a><a name="supports_cpu_shared_memory"></a>supports_cpu_shared_memory 

 获取一个布尔值，该值指示是否`accelerator`支持共享内存。  
  
```  
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;  
```  
  
##  <a name="a-namesupportsdoubleprecisiona-supportsdoubleprecision"></a><a name="supports_double_precision"></a>supports_double_precision 

 获取一个指示快捷键是否支持双精度算术的布尔值。  
  
```  
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;  
```  
  
##  <a name="a-namesupportslimiteddoubleprecisiona-supportslimiteddoubleprecision"></a><a name="supports_limited_double_precision"></a>supports_limited_double_precision 

 获取一个布尔值，指示快捷键是否限制了对双精度算术的支持。 如果快捷键仅提供有限的支持，则不支持融化乘法加法 (FMA)、除法以及 `int` 和 `double` 之间的相互转换。  
  
```  
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;  
```  
  
##  <a name="a-nameversiona-version"></a><a name="version"></a>版本 

 获取的版本`accelerator`。  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="dtor"></a></a> ~ accelerator_view 

 销毁[accelerator_view](accelerator-view-class.md)对象。  
  
```  
~accelerator_view();
```  
  
### <a name="return-value"></a>返回值  
  
##  <a name="a-nameacceleratora-accelerator"></a><a name="accelerator"></a>加速器 

 获取`accelerator`对象[accelerator_view](accelerator-view-class.md)对象。  
  
```  
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;  
```  
  
##  <a name="a-namectora-acceleratorview"></a><a name="ctor"></a>accelerator_view 

 新实例初始化[accelerator_view](accelerator-view-class.md)通过复制现有的类`accelerator_view`对象。  
  
```  
accelerator_view(const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `accelerator_view`要从中复制对象。  
  
##  <a name="a-namecreatemarkera-createmarker"></a><a name="create_marker"></a>create_marker 

 返回将来能够跟踪对此提交到目前为止的所有命令的完成`accelerator_view`对象。  
  
```  
concurrency::completion_future create_marker();
```  
  
### <a name="return-value"></a>返回值  
 将来能够跟踪对此提交到目前为止的所有命令的完成`accelerator_view`对象。  
  
##  <a name="a-nameflusha-flush"></a><a name="flush"></a>刷新 

 为排队的所有挂起命令提交[accelerator_view](accelerator-view-class.md)对象传递给快捷键执行。  
  
```  
void flush();
```  
  
### <a name="return-value"></a>返回值  
 返回 `void`。  
  
##  <a name="a-namegetacceleratora-getaccelerator"></a><a name="get_accelerator"></a>get_accelerator 

 返回`accelerator`对象[accelerator_view](accelerator-view-class.md)对象。  
  
```  
accelerator get_accelerator() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `accelerator`对象`accelerator_view`对象。  
  
##  <a name="a-namegetisautoselectiona-getisautoselection"></a><a name="get_is_auto_selection"></a>get_is_auto_selection 

 返回一个布尔值，该值指示是否 accelerator_view 传递给时，运行时将自动选择适当的加速器[parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each)。  
  
```  
bool get_is_auto_selection() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true`如果运行时将自动选择适当的加速器;否则为`false`。  
  
##  <a name="a-namegetisdebuga-getisdebug"></a><a name="get_is_debug"></a>get_is_debug 

 返回一个布尔值，该值指示是否[accelerator_view](accelerator-view-class.md)对象具有为广泛的错误报告启用了调试层。  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>返回值  
 一个布尔值，指示 `accelerator_view` 对象是否为广泛的错误报告启用了调试层。  
  
##  <a name="a-namegetqueuingmodea-getqueuingmode"></a><a name="get_queuing_mode"></a>get_queuing_mode 

 返回的排队模式[accelerator_view](accelerator-view-class.md)对象。  
  
```  
queuing_mode get_queuing_mode() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `accelerator_view` 对象的排队模式。  
  
##  <a name="a-namegetversiona-getversion"></a><a name="get_version"></a>get_version 

 返回的版本[accelerator_view](accelerator-view-class.md)。  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>返回值  
 版本`accelerator_view`。  
  
##  <a name="a-nameisautoselectiona-isautoselection"></a><a name="is_auto_selection"></a>is_auto_selection 

 获取一个布尔值，该值指示是否 accelerator_view 传递给时，运行时将自动选择适当的加速器[parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each)。  
  
```  
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;  
```  
  
##  <a name="a-nameisdebuga-isdebug"></a><a name="is_debug"></a>is_debug 

 获取一个布尔值，该值指示是否[accelerator_view](accelerator-view-class.md)对象具有为广泛的错误报告启用了调试层。  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="a-nameoperatorneqa-operator"></a><a name="operator_neq"></a>运算符 ！ = 

 比较此[accelerator_view](accelerator-view-class.md)与另一个对象，并返回`false`如果它们是相同的; 否则，返回`true`。  
  
```  
bool operator!= (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 与此对象相比较的 `accelerator_view` 对象。  
  
### <a name="return-value"></a>返回值  
 如果两个对象相同，则为 `false`；否则为 `true`。  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>运算符 = 

 将指定的内容复制[accelerator_view](accelerator-view-class.md)到此对象。  
  
```  
accelerator_view& operator= (const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `accelerator_view`从其中复制对象。  
  
### <a name="return-value"></a>返回值  
 对修改后的 `accelerator_view` 对象的引用。  
  
##  <a name="a-nameoperatoreqeqa-operator"></a><a name="operator_eq_eq"></a>运算符 = = 

 比较此[accelerator_view](accelerator-view-class.md)与另一个对象，并返回`true`如果它们是相同的; 否则，返回`false`。  
  
```  
bool operator== (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 与此对象相比较的 `accelerator_view` 对象。  
  
### <a name="return-value"></a>返回值  
 如果两个对象相同，则为 `true`；否则为 `false`。  
  
##  <a name="a-namequeuingmodea-queuingmode"></a><a name="queuing_mode"></a>queuing_mode 

 获取的排队模式[accelerator_view](accelerator-view-class.md)对象。  
  
```  
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;  
```  
  
##  <a name="a-nameversiona-version"></a><a name="version"></a>版本 

 获取的版本[accelerator_view](accelerator-view-class.md)。  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="a-namewaita-wait"></a><a name="wait"></a>等待 

 等待所有命令提交给[accelerator_view](accelerator-view-class.md)对象来完成。  
  
```  
void wait();
```  
  
### <a name="return-value"></a>返回值  
 返回 `void`。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace (c + + AMP)](concurrency-namespace-cpp-amp.md)


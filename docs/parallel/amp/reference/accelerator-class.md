---
title: "accelerator 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amprt/Concurrency::accelerator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "accelerator 类"
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# accelerator 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

加速器是针对数据并行计算进行了优化的硬件功能。 加速器可能是设备连接到 PCIe 总线 （如 GPU)，或者它可能在主 CPU 上设置的扩展的指令。  
  
## <a name="syntax"></a>语法  
  
```  
class accelerator;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[accelerator:: accelerator 构造函数](#accelerator__accelerator_constructor)|初始化 `accelerator` 类的新实例。|  
|[accelerator:: ~ accelerator 析构函数](#accelerator___dtoraccelerator_destructor)|销毁 `accelerator` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[accelerator:: create_view 方法](#accelerator__create_view_method)|创建并返回 `accelerator_view` 在此快捷键上的对象。|  
|[accelerator:: get_all 方法](#accelerator__get_all_method)|返回一个向量 `accelerator` 这些对象表示所有可用的快捷键。|  
|[accelerator:: get_auto_selection_view 方法](#accelerator__get_auto_selection_view_method)|返回自动选取 `accelerator_view`。|  
|[accelerator:: get_dedicated_memory 方法](#accelerator__get_dedicated_memory_method)|返回的专用的内存 `accelerator`, ，以千字节为单位。|  
|[accelerator:: get_default_cpu_access_type 方法](#accelerator__get_default_cpu_access_type_method)|返回的默认 [access_type](../Topic/concurrency%20namespace%20enums.md#access_type) 为在此快捷键上创建的缓冲区。|  
|[accelerator:: get_default_view 方法](#accelerator__get_default_view_method)|返回的默认 `accelerator_view` 与关联的对象 `accelerator`。|  
|[accelerator:: get_description 方法](#accelerator__get_description_method)|返回的简短说明 `accelerator` 设备。|  
|[accelerator:: get_device_path 方法](#accelerator__get_device_path_method)|返回该设备的路径。|  
|[accelerator:: get_has_display 方法](#accelerator__get_has_display_method)|确定是否 `accelerator` 附加到一个显示器。|  
|[accelerator:: get_is_debug 方法](#accelerator__get_is_debug_method)|确定是否 `accelerator` 为广泛的错误报告启用了调试层。|  
|[accelerator:: get_is_emulated 方法](#accelerator__get_is_emulated_method)|确定是否 `accelerator` 被模拟。|  
|[accelerator:: get_supports_cpu_shared_memory 方法](#accelerator__get_supports_cpu_shared_memory_method)|确定是否 `accelerator` 支持共享内存|  
|[accelerator:: get_supports_double_precision 方法](#accelerator__get_supports_double_precision_method)|确定是否 `accelerator` 附加到一个显示器。|  
|[accelerator:: get_supports_limited_double_precision 方法](#accelerator__get_supports_limited_double_precision_method)|确定是否 `accelerator` 提供有限的双精度算术的支持。|  
|[accelerator:: get_version 方法](#accelerator__get_version_method)|返回的版本 `accelerator`。|  
|[accelerator:: set_default 方法](#accelerator__set_default_method)|返回默认快捷键的路径。|  
|[accelerator:: set_default_cpu_access_type 方法](#accelerator__set_default_cpu_access_type_method)|设置默认 CPU [access_type](../Topic/concurrency%20namespace%20enums.md#access_type) 数组和对此进行隐式的内存分配 `accelerator`。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[accelerator:: operator ！ = 运算符](#accelerator__operator_neq_operator)|比较此 `accelerator` 与另一个对象，并返回 `false` 如果它们是相同的; 否则，返回 `true`。|  
|[accelerator:: operator = 运算符](#accelerator__operator_eq_operator)|将指定的内容复制 `accelerator` 对象传递给它。|  
|[accelerator:: operator = = 运算符](#accelerator__operator_eq_eq_operator)|比较此 `accelerator` 与另一个对象，并返回 `true` 如果它们是相同的; 否则，返回 `false`。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[accelerator:: cpu_accelerator 数据成员](#accelerator__cpu_accelerator_data_member)|获取一个字符串常数 CPU `accelerator`。|  
|[accelerator:: dedicated_memory 数据成员](#accelerator__dedicated_memory_data_member)|获取专用的内存 `accelerator`, ，以千字节为单位。|  
|[accelerator:: default_accelerator 数据成员](#accelerator__default_accelerator_data_member)|获取一个字符串常量默认 `accelerator`。|  
|[accelerator:: default_cpu_access_type 数据成员](#accelerator__default_cpu_access_type_data_member)|获取或设置默认 CPU [access_type](../Topic/concurrency%20namespace%20enums.md#access_type) 数组和对此进行隐式的内存分配 `accelerator`。|  
|[accelerator:: default_view 数据成员](#accelerator__default_view_data_member)|获取默认 `accelerator_view` 与关联的对象 `accelerator`。|  
|[accelerator:: description 数据成员](#accelerator__description_data_member)|获取的简短说明 `accelerator` 设备。|  
|[accelerator:: device_path 数据成员](#accelerator__device_path_data_member)|获取设备的路径。|  
|[accelerator:: direct3d_ref 数据成员](#accelerator__direct3d_ref_data_member)|获取 Direct3D 引用的字符串常量 `accelerator`。|  
|[accelerator:: direct3d_warp 数据成员](#accelerator__direct3d_warp_data_member)|获取的字符串常量， [加速器](../../../parallel/amp/reference/accelerator-class.md) 对象，您可将用于在使用流式处理 SIMD 扩展 (SSE) 的多核 Cpu 上执行 c + + AMP 代码。|  
|[accelerator:: has_display 数据成员](#accelerator__has_display_data_member)|获取一个布尔值，该值指示是否 `accelerator` 附加到一个显示器。|  
|[accelerator:: is_debug 数据成员](#accelerator__is_debug_data_member)|指示是否 `accelerator` 为广泛的错误报告启用了调试层。|  
|[accelerator:: is_emulated 数据成员](#accelerator__is_emulated_data_member)|指示是否 `accelerator` 被模拟。|  
|[accelerator:: supports_cpu_shared_memory 数据成员](#accelerator__supports_cpu_shared_memory_data_member)|指示是否 `accelerator` 支持共享内存。|  
|[accelerator:: supports_double_precision 数据成员](#accelerator__supports_double_precision_data_member)|指示快捷键是否支持双精度算术。|  
|[accelerator:: supports_limited_double_precision 数据成员](#accelerator__supports_limited_double_precision_data_member)|指示快捷键是否限制了对双精度算术的支持。|  
|[accelerator:: version 数据成员](#accelerator__version_data_member)|获取的版本 `accelerator`。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `accelerator`  
  
## <a name="remarks"></a>备注  
 加速器是针对数据并行计算进行了优化的硬件功能。 加速器通常是离散的 GPU，但它也可以是虚拟的宿主端实体，如一种变形 （的 CPU 端设备通过 SSE 指令加速） 或 CPU 自身的 DirectX REF 设备。  
  
 您可以构造 `accelerator` 通过枚举可用的设备，或通过获取默认的设备、 引用设备或 WARP 设备对象。  
  
## <a name="requirements"></a>要求  
 **标头︰** amprt.h  
  
 **命名空间：** 并发  
  
##  <a name="a-nameacceleratordtoracceleratordestructora-acceleratoraccelerator-destructor"></a><a name="accelerator___dtoraccelerator_destructor"></a>  accelerator:: ~ accelerator 析构函数  
 销毁 [加速器](../../../parallel/amp/reference/accelerator-class.md) 对象。  
  
```  
~accelerator();
```  
  
### <a name="return-value"></a>返回值  
  
##  <a name="a-nameacceleratoracceleratorconstructora-acceleratoraccelerator-constructor"></a><a name="accelerator__accelerator_constructor"></a>  accelerator:: accelerator 构造函数  
 新实例初始化 [accelerator 类](../../../parallel/amp/reference/accelerator-class.md)。  
  
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
  
##  <a name="a-nameacceleratorcpuacceleratordatamembera-acceleratorcpuaccelerator-data-member"></a><a name="accelerator__cpu_accelerator_data_member"></a>  accelerator:: cpu_accelerator 数据成员  
 获取 CPU 快捷键的字符串常数。  
  
```  
static const wchar_t cpu_accelerator[];  
```  
  
##  <a name="a-nameacceleratorcreateviewmethoda-acceleratorcreateview-method"></a><a name="accelerator__create_view_method"></a>  accelerator:: create_view 方法  
 使用指定的排队模式，在快捷键上创建并返回一个 `accelerator_view` 对象。 如果未指定排队模式，新 `accelerator_view` 使用 [queuing_mode:: immediate](../Topic/concurrency%20namespace%20enums.md#queuing_mode) 排队模式。  
  
```  
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```  
  
### <a name="parameters"></a>参数  
 `qmode`  
 排队模式。  
  
### <a name="return-value"></a>返回值  
 使用指定队列的模式，在此快捷键上创建的新 `accelerator_view` 对象。  
  
##  <a name="a-nameacceleratordedicatedmemorydatamembera-acceleratordedicatedmemory-data-member"></a><a name="accelerator__dedicated_memory_data_member"></a>  accelerator:: dedicated_memory 数据成员  
 获取专用的内存 [加速器](../../../parallel/amp/reference/accelerator-class.md), ，以千字节为单位。  
  
```  
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;  
```  
  
##  <a name="a-nameacceleratordefaultacceleratordatamembera-acceleratordefaultaccelerator-data-member"></a><a name="accelerator__default_accelerator_data_member"></a>  accelerator:: default_accelerator 数据成员  
 获取一个字符串常量默认 [加速器](../../../parallel/amp/reference/accelerator-class.md)。  
  
```  
static const wchar_t default_accelerator[];  
```  
  
##  <a name="a-nameacceleratordefaultcpuaccesstypedatamembera-acceleratordefaultcpuaccesstype-data-member"></a><a name="accelerator__default_cpu_access_type_data_member"></a>  accelerator:: default_cpu_access_type 数据成员  
 默认值 cpu [access_type](../Topic/concurrency%20namespace%20enums.md#access_type) 数组和此内容进行隐式的内存分配 `accelerator`。  
  
```  
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;  
```  
  
##  <a name="a-nameacceleratordefaultviewdatamembera-acceleratordefaultview-data-member"></a><a name="accelerator__default_view_data_member"></a>  accelerator:: default_view 数据成员  
 获取与之关联的默认快捷键视图 [加速器](../../../parallel/amp/reference/accelerator-class.md)。  
  
```  
__declspec(property(get= get_default_view)) accelerator_view default_view;  
```  
  
##  <a name="a-nameacceleratordescriptiondatamembera-acceleratordescription-data-member"></a><a name="accelerator__description_data_member"></a>  accelerator:: description 数据成员  
 获取的简短说明 [加速器](../../../parallel/amp/reference/accelerator-class.md) 设备。  
  
```  
__declspec(property(get= get_description)) std::wstring description;  
```  
  
##  <a name="a-nameacceleratordevicepathdatamembera-acceleratordevicepath-data-member"></a><a name="accelerator__device_path_data_member"></a>  accelerator:: device_path 数据成员  
 获取快捷键的路径。 该路径在系统上是唯一的。  
  
```  
__declspec(property(get= get_device_path)) std::wstring device_path;  
```  
  
##  <a name="a-nameacceleratordirect3drefdatamembera-acceleratordirect3dref-data-member"></a><a name="accelerator__direct3d_ref_data_member"></a>  accelerator:: direct3d_ref 数据成员  
 获取 Direct3D 引用快捷键的字符串常数。  
  
```  
static const wchar_t direct3d_ref[];  
```  
  
##  <a name="a-nameacceleratordirect3dwarpdatamembera-acceleratordirect3dwarp-data-member"></a><a name="accelerator__direct3d_warp_data_member"></a>  accelerator:: direct3d_warp 数据成员  
 获取的字符串常量， [加速器](../../../parallel/amp/reference/accelerator-class.md) 对象，您可将用于使用流式处理 SIMD 扩展 (SSE) 的多核 Cpu 上执行 c + + AMP 代码。  
  
```  
static const wchar_t direct3d_warp[];  
```  
  
##  <a name="a-nameacceleratorgetallmethoda-acceleratorgetall-method"></a><a name="accelerator__get_all_method"></a>  accelerator:: get_all 方法  
 返回一个向量 `accelerator` 这些对象表示所有可用的快捷键。  
  
```  
static inline std::vector<accelerator> get_all();
```  
  
### <a name="return-value"></a>返回值  
 可用快捷键的矢量  
  
##  <a name="a-nameacceleratorgetautoselectionviewmethoda-acceleratorgetautoselectionview-method"></a><a name="accelerator__get_auto_selection_view_method"></a>  accelerator:: get_auto_selection_view 方法  
 返回自动选择 accelerator_view，当指定为用于执行要由运行时自动选择的 parallel_for_each 内核目标 accelerator_view parallel_for_each 目标结果。 用于其他目的，此方法返回 accelerator_view 等同于默认快捷键默认 accelerator_view  
  
```  
static accelerator_view __cdecl get_auto_selection_view();
```  
  
### <a name="return-value"></a>返回值  
 自动选择 accelerator_view。  
  
##  <a name="a-nameacceleratorgetdedicatedmemorymethoda-acceleratorgetdedicatedmemory-method"></a><a name="accelerator__get_dedicated_memory_method"></a>  accelerator:: get_dedicated_memory 方法  
 返回的专用的内存 [加速器](../../../parallel/amp/reference/accelerator-class.md), ，以千字节为单位。  
  
```  
size_t get_dedicated_memory() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `accelerator` 的专用内存（单位为 KB）。  
  
##  <a name="a-nameacceleratorgetdefaultcpuaccesstypemethoda-acceleratorgetdefaultcpuaccesstype-method"></a><a name="accelerator__get_default_cpu_access_type_method"></a>  accelerator:: get_default_cpu_access_type 方法  
 获取在此快捷键上创建的缓冲区的默认 cpu access_type  
  
```  
access_type get_default_cpu_access_type() const;

 
```  
  
### <a name="return-value"></a>返回值  
 在此快捷键上创建的缓冲区默认 cpu access_type。  
  
##  <a name="a-nameacceleratorgetdefaultviewmethoda-acceleratorgetdefaultview-method"></a><a name="accelerator__get_default_view_method"></a>  accelerator:: get_default_view 方法  
 返回的默认 `accelerator_view` 与关联的对象 [加速器](../../../parallel/amp/reference/accelerator-class.md)。  
  
```  
accelerator_view get_default_view() const;

 
```  
  
### <a name="return-value"></a>返回值  
 与 `accelerator_view` 关联的默认 `accelerator` 对象。  
  
##  <a name="a-nameacceleratorgetdescriptionmethoda-acceleratorgetdescription-method"></a><a name="accelerator__get_description_method"></a>  accelerator:: get_description 方法  
 返回的简短说明 [加速器](../../../parallel/amp/reference/accelerator-class.md) 设备。  
  
```  
std::wstring get_description() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `accelerator` 设备的简短说明。  
  
##  <a name="a-nameacceleratorgetdevicepathmethoda-acceleratorgetdevicepath-method"></a><a name="accelerator__get_device_path_method"></a>  accelerator:: get_device_path 方法  
 返回快捷键的路径。 该路径在系统上是唯一的。  
  
```  
std::wstring get_device_path() const;

 
```  
  
### <a name="return-value"></a>返回值  
 系统范围内唯一的设备实例路径。  
  
##  <a name="a-nameacceleratorgethasdisplaymethoda-acceleratorgethasdisplay-method"></a><a name="accelerator__get_has_display_method"></a>  accelerator:: get_has_display 方法  
 返回一个布尔值，该值指示是否 [加速器](../../../parallel/amp/reference/accelerator-class.md) 可以输出到显示器。  
  
```  
bool get_has_display() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果 `accelerator` 可以输出到显示器; 否则为 `false`。  
  
##  <a name="a-nameacceleratorgetisdebugmethoda-acceleratorgetisdebug-method"></a><a name="accelerator__get_is_debug_method"></a>  accelerator:: get_is_debug 方法  
 确定是否 [加速器](../../../parallel/amp/reference/accelerator-class.md) 为广泛的错误报告启用了调试层。  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果 `accelerator` 为广泛的错误报告启用了调试层。 否则为 `false`。  
  
##  <a name="a-nameacceleratorgetisemulatedmethoda-acceleratorgetisemulated-method"></a><a name="accelerator__get_is_emulated_method"></a>  accelerator:: get_is_emulated 方法  
 确定是否 [加速器](../../../parallel/amp/reference/accelerator-class.md) 被模拟。  
  
```  
bool get_is_emulated() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果 `accelerator` 被模拟。 否则为 `false`。  
  
##  <a name="a-nameacceleratorgetsupportscpusharedmemorymethoda-acceleratorgetsupportscpusharedmemory-method"></a><a name="accelerator__get_supports_cpu_shared_memory_method"></a>  accelerator:: get_supports_cpu_shared_memory 方法  
 返回一个布尔值，该值指示快捷键是否支持内存都可访问，同时通过加速器和 CPU。  
  
```  
bool get_supports_cpu_shared_memory() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果快捷键支持 CPU 共享内存;否则为 `false`。  
  
##  <a name="a-nameacceleratorgetsupportsdoubleprecisionmethoda-acceleratorgetsupportsdoubleprecision-method"></a><a name="accelerator__get_supports_double_precision_method"></a>  accelerator:: get_supports_double_precision 方法  
 返回一个布尔值，该值指示是否加速器支持双精度算术，包括融化乘法加法 (FMA)、 除法以及相互之间的强制转换 `int` 和 `double`。  
  
```  
bool get_supports_double_precision() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果快捷键支持双精度算术;否则为 `false`。  
  
##  <a name="a-nameacceleratorgetsupportslimiteddoubleprecisionmethoda-acceleratorgetsupportslimiteddoubleprecision-method"></a><a name="accelerator__get_supports_limited_double_precision_method"></a>  accelerator:: get_supports_limited_double_precision 方法  
 返回一个布尔值，指示快捷键是否限制了对双精度算术的支持。 如果快捷键仅提供有限的支持，则不支持融化乘法加法 (FMA)、除法以及 `int` 和 `double` 之间的相互转换。  
  
```  
bool get_supports_limited_double_precision() const;

 
```  
  
### <a name="return-value"></a>返回值  
 如果快捷键对双精度算术只提供有限的支持，则为 `true`；否则为 `false`。  
  
##  <a name="a-nameacceleratorgetversionmethoda-acceleratorgetversion-method"></a><a name="accelerator__get_version_method"></a>  accelerator:: get_version 方法  
 返回的版本 [加速器](../../../parallel/amp/reference/accelerator-class.md)。  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>返回值  
 版本 `accelerator`。  
  
##  <a name="a-nameacceleratorhasdisplaydatamembera-acceleratorhasdisplay-data-member"></a><a name="accelerator__has_display_data_member"></a>  accelerator:: has_display 数据成员  
 获取一个布尔值，该值指示是否 [加速器](../../../parallel/amp/reference/accelerator-class.md) 可以输出到显示器。  
  
```  
__declspec(property(get= get_has_display)) bool has_display;  
```  
  
##  <a name="a-nameacceleratorisdebugdatamembera-acceleratorisdebug-data-member"></a><a name="accelerator__is_debug_data_member"></a>  accelerator:: is_debug 数据成员  
 获取一个布尔值，该值指示是否 [加速器](../../../parallel/amp/reference/accelerator-class.md) 为广泛的错误报告启用了调试层。  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="a-nameacceleratorisemulateddatamembera-acceleratorisemulated-data-member"></a><a name="accelerator__is_emulated_data_member"></a>  accelerator:: is_emulated 数据成员  
 获取一个布尔值，该值指示是否 [加速器](../../../parallel/amp/reference/accelerator-class.md) 被模拟。  
  
```  
__declspec(property(get= get_is_emulated)) bool is_emulated;  
```  
  
##  <a name="a-nameacceleratoroperatorneqoperatora-acceleratoroperator-operator"></a><a name="accelerator__operator_neq_operator"></a>  accelerator:: operator ！ = 运算符  
 比较此 `accelerator` 与另一个对象，并返回 `false` 如果它们是相同的; 否则，返回 `true`。  
  
```  
bool operator!= (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 与此对象相比较的 `accelerator` 对象。  
  
### <a name="return-value"></a>返回值  
 `false` 如果两个 `accelerator` 对象是否相同; 否则为 `true`。  
  
##  <a name="a-nameacceleratoroperatoreqoperatora-acceleratoroperator-operator"></a><a name="accelerator__operator_eq_operator"></a>  accelerator:: operator = 运算符  
 将指定的内容复制 [加速器](../../../parallel/amp/reference/accelerator-class.md) 对象传递给它。  
  
```  
accelerator& operator= (const accelerator& _Other);
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
  `accelerator` 从其中复制对象。  
  
### <a name="return-value"></a>返回值  
 参考这 `accelerator` 对象。  
  
##  <a name="a-nameacceleratoroperatoreqeqoperatora-acceleratoroperator-operator"></a><a name="accelerator__operator_eq_eq_operator"></a>  accelerator:: operator = = 运算符  
 比较此 [加速器](../../../parallel/amp/reference/accelerator-class.md) 与另一个对象，并返回 `true` 如果它们是相同的; 否则，返回 `false`。  
  
```  
bool operator== (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 与此对象相比较的 `accelerator` 对象。  
  
### <a name="return-value"></a>返回值  
 `true` 如果其他 `accelerator` 对象是与此相同 `accelerator` 对象; 否则为 `false`。  
  
##  <a name="a-nameacceleratorsetdefaultmethoda-acceleratorsetdefault-method"></a><a name="accelerator__set_default_method"></a>  accelerator:: set_default 方法  
 设置默认快捷键用于隐式地使用默认快捷键的任何操作。 此方法才会成功运行时所选的默认快捷键具有已中尚未使用隐式使用默认快捷键的操作  
  
```  
static inline bool set_default(std::wstring _Path);
```  
  
### <a name="parameters"></a>参数  
 `_Path`  
 指向快捷键的路径。  
  
### <a name="return-value"></a>返回值  
 `true` 如果调用成功保持设置默认快捷键。 否则为 `false`。  
  
##  <a name="a-nameacceleratorsetdefaultcpuaccesstypemethoda-acceleratorsetdefaultcpuaccesstype-method"></a><a name="accelerator__set_default_cpu_access_type_method"></a>  accelerator:: set_default_cpu_access_type 方法  
 设置默认 cpu access_type array_views 的一部分对此此加速器访问创建在此快捷键上或用于隐式的内存分配的数组。 此方法才会成功。 如果加速器 default_cpu_access_type 尚未被重写此方法的以前调用，并且分配了数组或备份在此快捷键上访问 array_view 执行隐式的内存分配以前未被使用此加速器所选的运行时 default_cpu_access_type。  
  
```  
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```  
  
### <a name="parameters"></a>参数  
 `_Default_cpu_access_type`  
 要用于在此快捷键上数组/array_view 内存分配默认 cpu access_type。  
  
### <a name="return-value"></a>返回值  
 一个布尔值，该值指示快捷键默认 cpu access_type 已成功设置。  
  
##  <a name="a-nameacceleratorsupportscpusharedmemorydatamembera-acceleratorsupportscpusharedmemory-data-member"></a><a name="accelerator__supports_cpu_shared_memory_data_member"></a>  accelerator:: supports_cpu_shared_memory 数据成员  
 获取一个布尔值，该值指示是否 `accelerator` 支持共享内存。  
  
```  
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;  
```  
  
##  <a name="a-nameacceleratorsupportsdoubleprecisiondatamembera-acceleratorsupportsdoubleprecision-data-member"></a><a name="accelerator__supports_double_precision_data_member"></a>  accelerator:: supports_double_precision 数据成员  
 获取一个指示快捷键是否支持双精度算术的布尔值。  
  
```  
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;  
```  
  
##  <a name="a-nameacceleratorsupportslimiteddoubleprecisiondatamembera-acceleratorsupportslimiteddoubleprecision-data-member"></a><a name="accelerator__supports_limited_double_precision_data_member"></a>  accelerator:: supports_limited_double_precision 数据成员  
 获取一个布尔值，指示快捷键是否限制了对双精度算术的支持。 如果快捷键仅提供有限的支持，则不支持融化乘法加法 (FMA)、除法以及 `int` 和 `double` 之间的相互转换。  
  
```  
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;  
```  
  
##  <a name="a-nameacceleratorversiondatamembera-acceleratorversion-data-member"></a><a name="accelerator__version_data_member"></a>  accelerator:: version 数据成员  
 获取的版本 [加速器](../../../parallel/amp/reference/accelerator-class.md)。  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="a-nameacceleratorviewdtoracceleratorviewdestructora-acceleratorviewacceleratorview-destructor"></a><a name="accelerator_view___dtoraccelerator_view_destructor"></a>  accelerator_view:: ~ accelerator_view 析构函数  
 销毁 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 对象。  
  
```  
~accelerator_view();
```  
  
### <a name="return-value"></a>返回值  
  
##  <a name="a-nameacceleratorviewacceleratordatamembera-acceleratorviewaccelerator-data-member"></a><a name="accelerator_view__accelerator_data_member"></a>  accelerator_view:: accelerator 数据成员  
 获取 [加速器](../../../parallel/amp/reference/accelerator-class.md) 对象 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 对象。  
  
```  
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;  
```  
  
##  <a name="a-nameacceleratorviewacceleratorviewconstructora-acceleratorviewacceleratorview-constructor"></a><a name="accelerator_view__accelerator_view_constructor"></a>  accelerator_view:: accelerator_view 构造函数  
 新实例初始化 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 通过复制现有的类 `accelerator_view` 对象。  
  
```  
accelerator_view(const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
  `accelerator_view` 要从中复制对象。  
  
##  <a name="a-nameacceleratorviewcreatemarkermethoda-acceleratorviewcreatemarker-method"></a><a name="accelerator_view__create_marker_method"></a>  accelerator_view:: create_marker 方法  
 返回将来能够跟踪对此提交到目前为止的所有命令的完成 `accelerator_view` 对象。  
  
```  
concurrency::completion_future create_marker();
```  
  
### <a name="return-value"></a>返回值  
 将来能够跟踪对此提交到目前为止的所有命令的完成 `accelerator_view` 对象。  
  
##  <a name="a-nameacceleratorviewflushmethoda-acceleratorviewflush-method"></a><a name="accelerator_view__flush_method"></a>  accelerator_view:: flush 方法  
 为排队的所有挂起命令提交 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 对象传递给快捷键执行。  
  
```  
void flush();
```  
  
### <a name="return-value"></a>返回值  
 返回 `void`。  
  
##  <a name="a-nameacceleratorviewgetacceleratormethoda-acceleratorviewgetaccelerator-method"></a><a name="accelerator_view__get_accelerator_method"></a>  accelerator_view:: get_accelerator 方法  
 返回 [加速器](../../../parallel/amp/reference/accelerator-class.md) 对象 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 对象。  
  
```  
accelerator get_accelerator() const;

 
```  
  
### <a name="return-value"></a>返回值  
  `accelerator` 对象 `accelerator_view` 对象。  
  
##  <a name="a-nameacceleratorviewgetisautoselectionmethoda-acceleratorviewgetisautoselection-method"></a><a name="accelerator_view__get_is_auto_selection_method"></a>  accelerator_view:: get_is_auto_selection 方法  
 返回一个布尔值，该值指示是否 accelerator_view 传递给时，运行时将自动选择适当的加速器 [parallel_for_each](../Topic/concurrency%20namespace%20functions.md#parallel_for_each)。  
  
```  
bool get_is_auto_selection() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果运行时将自动选择适当的加速器;否则为 `false`。  
  
##  <a name="a-nameacceleratorviewgetisdebugmethoda-acceleratorviewgetisdebug-method"></a><a name="accelerator_view__get_is_debug_method"></a>  accelerator_view:: get_is_debug 方法  
 返回一个布尔值，该值指示是否 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 对象具有为广泛的错误报告启用了调试层。  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>返回值  
 一个布尔值，指示 `accelerator_view` 对象是否为广泛的错误报告启用了调试层。  
  
##  <a name="a-nameacceleratorviewgetqueuingmodemethoda-acceleratorviewgetqueuingmode-method"></a><a name="accelerator_view__get_queuing_mode_method"></a>  accelerator_view:: get_queuing_mode 方法  
 返回的排队模式 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 对象。  
  
```  
queuing_mode get_queuing_mode() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `accelerator_view` 对象的排队模式。  
  
##  <a name="a-nameacceleratorviewgetversionmethoda-acceleratorviewgetversion-method"></a><a name="accelerator_view__get_version_method"></a>  accelerator_view:: get_version 方法  
 返回的版本 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md)。  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>返回值  
 版本 `accelerator_view`。  
  
##  <a name="a-nameacceleratorviewisautoselectiondatamembera-acceleratorviewisautoselection-data-member"></a><a name="accelerator_view__is_auto_selection_data_member"></a>  accelerator_view:: is_auto_selection 数据成员  
 获取一个布尔值，该值指示是否 accelerator_view 传递给时，运行时将自动选择适当的加速器 [parallel_for_each](concurrency%20namespace%20functions.md#parallel_for_each)。  
  
```  
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;  
```  
  
##  <a name="a-nameacceleratorviewisdebugdatamembera-acceleratorviewisdebug-data-member"></a><a name="accelerator_view__is_debug_data_member"></a>  accelerator_view:: is_debug 数据成员  
 获取一个布尔值，该值指示是否 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 对象具有为广泛的错误报告启用了调试层。  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="a-nameacceleratorviewoperatorneqoperatora-acceleratorviewoperator-operator"></a><a name="accelerator_view__operator_neq_operator"></a>  accelerator_view:: operator ！ = 运算符  
 比较此 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 与另一个对象，并返回 `false` 如果它们是相同的; 否则，返回 `true`。  
  
```  
bool operator!= (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 与此对象相比较的 `accelerator_view` 对象。  
  
### <a name="return-value"></a>返回值  
 如果两个对象相同，则为 `false`；否则为 `true`。  
  
##  <a name="a-nameacceleratorviewoperatoreqoperatora-acceleratorviewoperator-operator"></a><a name="accelerator_view__operator_eq_operator"></a>  accelerator_view:: operator = 运算符  
 将指定的内容复制 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 到此对象。  
  
```  
accelerator_view& operator= (const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
  `accelerator_view` 从其中复制对象。  
  
### <a name="return-value"></a>返回值  
 对修改后的 `accelerator_view` 对象的引用。  
  
##  <a name="a-nameacceleratorviewoperatoreqeqoperatora-acceleratorviewoperator-operator"></a><a name="accelerator_view__operator_eq_eq_operator"></a>  accelerator_view:: operator = = 运算符  
 比较此 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 与另一个对象，并返回 `true` 如果它们是相同的; 否则，返回 `false`。  
  
```  
bool operator== (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 与此对象相比较的 `accelerator_view` 对象。  
  
### <a name="return-value"></a>返回值  
 如果两个对象相同，则为 `true`；否则为 `false`。  
  
##  <a name="a-nameacceleratorviewqueuingmodedatamembera-acceleratorviewqueuingmode-data-member"></a><a name="accelerator_view__queuing_mode_data_member"></a>  accelerator_view:: queuing_mode 数据成员  
 获取的排队模式 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 对象。  
  
```  
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;  
```  
  
##  <a name="a-nameacceleratorviewversiondatamembera-acceleratorviewversion-data-member"></a><a name="accelerator_view__version_data_member"></a>  accelerator_view:: version 数据成员  
 获取的版本 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md)。  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="a-nameacceleratorviewwaitmethoda-acceleratorviewwait-method"></a><a name="accelerator_view__wait_method"></a>  accelerator_view:: wait 方法  
 等待所有命令提交给 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 对象来完成。  
  
```  
void wait();
```  
  
### <a name="return-value"></a>返回值  
 返回 `void`。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace (c + + AMP)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)

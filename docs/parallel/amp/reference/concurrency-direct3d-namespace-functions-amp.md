---
title: 'Concurrency:: direct3d 命名空间函数 (AMP) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- amp/Concurrency::direct3d::abs
- amp/Concurrency::direct3d::countbits
- amp/Concurrency::direct3d::create_accelerator_view
- amp/Concurrency::direct3d::d3d_access_lock
- amp/Concurrency::direct3d::d3d_access_unlock
- amp/Concurrency::direct3d::firstbithigh
- amp/Concurrency::direct3d::get_buffer
- amp/Concurrency::direct3d::imax
- amp/Concurrency::direct3d::is_timeout_disabled
- amp/Concurrency::direct3d::mad
- amp/Concurrency::direct3d::noise
- amp/Concurrency::direct3d::radians
- amp/Concurrency::direct3d::reversebits
- amp/Concurrency::direct3d::saturate
- amp/Concurrency::direct3d::smoothstep
- amp/Concurrency::direct3d::step
- amp/Concurrency::direct3d::umin
dev_langs:
- C++
ms.assetid: 28943b62-52c9-42dc-baf1-ca7b095c1a19
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b200ce8329c10fe2257ca3ce9ca8cb61125390fc
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/10/2018
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency:: direct3d 命名空间函数 (AMP)
||||  
|-|-|-|  
|[abs](#abs)|[clamp](#clamp)|[countbits](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|||
|[d3d_access_lock](#d3d_access_lock)|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|  
|[firstbithigh](#firstbithigh)|[firstbitlow](#firstbitlow)|[get_buffer](#get_buffer)|  
|[imax](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|  
|[mad](#mad)|[make_array](#make_array)|[noise](#noise)|  
|[radians](#radians)|[rcp](#rcp)|[reversebits](#reversebits)|  
|[saturate](#saturate)|[sign](#sign)|[smoothstep](#smoothstep)|  
|[step](#step)|[umax](#umax)|[umin](#umin)|  

## <a name="requirements"></a>要求
**标头：** amp.h **Namespace:**并发
  
##  <a name="abs"></a>  abs  
 返回自变量的绝对值  
  
```  
inline int abs(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 整数值  
  
### <a name="return-value"></a>返回值  
 返回自变量的绝对值。  
  
##  <a name="clamp"></a>  clamp  
 计算其限制为第二个和第三个指定的参数定义范围内第一个指定自变量的值。  
  
```  
inline float clamp(
    float _X,  
    float _Min,  
    float _Max) restrict(amp);

 
inline int clamp(
    int _X,  
    int _Min,  
    int _Max) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 要被限制的值  
  
 `_Min`  
 夹紧范围的下限。  
  
 `_Max`  
 夹紧范围的上限。  
  
### <a name="return-value"></a>返回值  
 限制的值`_X`。  
  
##  <a name="countbits"></a>  countbits  
 计算 _X 中设置位的数目  
  
```  
inline unsigned int countbits(unsigned int _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 无符号整数值  
  
### <a name="return-value"></a>返回值  
 返回 _X 中的一组比特数  

## <a name="create_accelerator_view"></a> create_accelerator_view  
创建[accelerator_view](accelerator-view-class.md)从指针到 Direct3D 设备接口的对象。  
  
## <a name="syntax"></a>语法  
  
```  
accelerator_view create_accelerator_view(  
    IUnknown * _D3D_device  
    queuing_mode _Qmode = queuing_mode_automatic);  
  
accelerator_view create_accelerator_view(  
    accelerator& _Accelerator,  
    bool _Disable_timeout  
    queuing_mode _Qmode = queuing_mode_automatic);  
```  
  
#### <a name="parameters"></a>参数  
 `_Accelerator`  
 新 accelerator_view 是要创建快捷键。  
  
 `_D3D_device`  
 指向 Direct3D 设备接口的指针。  
  
 `_Disable_timeout`  
 一个布尔型参数，用于指定是否应为新创建的 accelerator_view 禁用超时。 这对应于用于创建 Direct3D 设备的 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 标志，用于指示操作系统应允许采取多个 2 秒，执行，而每个 Windows 超时将设备重置的工作负荷检测和恢复机制。 如果你需要在 accelerator_view 上执行耗时的任务，则建议使用此标志。  
  
 `_Qmode`  
 [Queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)要用于新创建的 accelerator_view。 此参数具有默认值为`queuing_mode_automatic`。  
  
## <a name="return-value"></a>返回值  
 `accelerator_view`创建来自传入 Direct3D 设备接口的对象。  
  
## <a name="remarks"></a>备注  
 此函数会创建一个新`accelerator_view`从现有指针到 Direct3D 设备接口的对象。 如果函数调用成功，该参数的引用计数会递增的方式`AddRef`调用界面。 不再需要 DirectX 代码中时，你可以安全地释放该对象。 如果方法调用失败， [runtime_exception](runtime-exception-class.md)引发。  
  
 `accelerator_view`通过使用此函数创建的对象是线程安全的。 你必须同步并发使用`accelerator_view`对象。 未同步的并发使用`accelerator_view`对象和原始 ID3D11Device 接口会导致未定义的行为。  
  
 C + + AMP 运行时提供详细的错误信息，在调试模式下使用 D3D 调试层，如果你使用`D3D11_CREATE_DEVICE_DEBUG`标志。  
  
  
##  <a name="d3d_access_lock"></a>  d3d_access_lock  
 获取对安全地执行与 accelerator_view 共享的资源执行 D3D 操作各种非法 accelerator_view 的锁。 Accelerator_view 和内部与此 accelerator_view 相关联的所有 c + + AMP 资源考虑此锁，执行操作时，将阻止另一个线程保持 D3D 访问锁。 此锁，则非递归： 它是未定义的行为，从已持有锁的线程调用此函数。 它是未定义的行为在 accelerator_view 或任何从持有 D3D 访问锁的线程 accelerator_view 与关联的数据容器上执行操作。 另请参阅 scoped_d3d_access_lock，基于范围的 D3D 访问锁 RAII 样式类。  
  
```  
void __cdecl d3d_access_lock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>参数  
 `_Av`  
 若要锁定 accelerator_view。  
  
##  <a name="d3d_access_try_lock"></a>  d3d_access_try_lock  
 尝试获取对 accelerator_view 的 D3D 访问锁定而不阻止。  
  
```  
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>参数  
 `_Av`  
 若要锁定 accelerator_view。  
  
### <a name="return-value"></a>返回值  
 如果已获取锁，则为 true 或 false，如果它当前由另一个线程。  
  
##  <a name="d3d_access_unlock"></a>  d3d_access_unlock  
 释放 D3D 访问锁在给定的 accelerator_view 上。 如果调用线程 accelerator_view 不保持锁定，结果不确定。  
  
```  
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>参数  
 `_Av`  
 Accelerator_view，为释放锁。  
  
##  <a name="firstbithigh"></a>  firstbithigh  
 获取 _X，开头最高顺序位并转向最低顺序位中的第一个设置位的位置。  
  
```  
inline int firstbithigh(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 整数值  
  
### <a name="return-value"></a>返回值  
 第一个设置位的位置  
  
##  <a name="firstbitlow"></a>  firstbitlow  
 获取 _X，开头最低顺序位并围绕最高顺序位工作中的第一个设置位的位置。  
  
```  
inline int firstbitlow(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 整数值  
  
### <a name="return-value"></a>返回值  
 返回的第一个设置位的位置  
  
##  <a name="get_buffer"></a>  get_buffer  
 获取 Direct3D 缓冲区接口基础指定的数组。  
  
```  
template<
    typename value_type,  
    int _Rank  
>  
IUnknown *get_buffer(
    const array<value_type, _Rank>& _Array)  ;  
```  
  
### <a name="parameters"></a>参数  
 `value_type`  
 数组中元素的类型。  
  
 `_Rank`  
 数组的秩。  
  
 `_Array`  
 在为其返回基础 Direct3D 缓冲区接口 Direct3D accelerator_view 数组。  
  
### <a name="return-value"></a>返回值  
 对应于基础数组的 Direct3D 缓冲区 IUnknown 接口指针。  
  
##  <a name="imax"></a>  imax  
 确定自变量的最大数值  
  
```  
inline int imax(
    int _X,  
    int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 整数值  
  
 `_Y`  
 整数值  
  
### <a name="return-value"></a>返回值  
 返回自变量的最大数值  
  
##  <a name="imin"></a>  imin  
 确定自变量的最小数值  
  
```  
inline int imin(
    int _X,  
    int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 整数值  
  
 `_Y`  
 整数值  
  
### <a name="return-value"></a>返回值  
 返回自变量的最小数值  
  
##  <a name="is_timeout_disabled"></a>  is_timeout_disabled  
 返回一个布尔型标志，该值指示是否对指定 accelerator_view 禁用超时。 这对应于用于创建 Direct3D 设备的 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 标志。  
  
```  
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```  
  
### <a name="parameters"></a>参数  
 `_Accelerator_view`  
 Accelerator_view，为查询设置禁用的超时值。  
  
### <a name="return-value"></a>返回值  
 一个布尔型标志，该值指示是否对指定 accelerator_view 禁用超时。  
  
##  <a name="mad"></a>  mad  
 计算产品的第一个和第二个指定的自变量，然后添加第三个指定的自变量。  
  
```  
inline float mad(
    float _X,  
    float _Y,  
    float _Z) restrict(amp);

 
inline double mad(
    double _X,  
    double _Y,  
    double _Z) restrict(amp);

 
inline int mad(
    int _X,  
    int _Y,  
    int _Z) restrict(amp);

 
inline unsigned int mad(
    unsigned int _X,  
    unsigned int _Y,  
    unsigned int _Z) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 第一个指定自变量。  
  
 `_Y`  
 第二个指定的自变量。  
  
 `_Z`  
 第三个指定的自变量。  
  
### <a name="return-value"></a>返回值  
 结果`_X`  *  `_Y`  +  `_Z`。  
  
##  <a name="make_array"></a>  make_array  
 创建从 Direct3D 缓冲区接口指针的数组。  
  
```  
template<
    typename value_type,  
    int _Rank  
>  
array<value_type, _Rank> make_array(
    const extent<_Rank>& _Extent,  
    const Concurrency::accelerator_view& _Rv,  
    IUnknown* _D3D_buffer)  ;  
```  
  
### <a name="parameters"></a>参数  
 `value_type`  
 要创建的数组元素类型。  
  
 `_Rank`  
 要创建数组的秩。  
  
 `_Extent`  
 介绍数组聚合的形状的范围。  
  
 `_Rv`  
 数组是要创建 D3D 快捷键视图。  
  
 `_D3D_buffer`  
 要创建从数组的 D3D 缓冲区的 IUnknown 接口指针。  
  
### <a name="return-value"></a>返回值  
 使用提供的 Direct3D 缓冲区创建数组。  
  
##  <a name="noise"></a>  noise  
 通过采用 Perlin 噪音算法生成一个随机值  
  
```  
inline float noise(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 从其生成 Perlin 噪音的浮点值  
  
### <a name="return-value"></a>返回值  
 返回在一个介于 -1 和 1 之间的 Perlin 噪音值  
  
##  <a name="radians"></a>  radians  
 将 _X 从度数转换成弧度  
  
```  
inline float radians(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回从度数转换到弧度的 _X。  
  
##  <a name="rcp"></a>  rcp  
 通过使用快速近似计算指定的自变量的倒数。  
  
```  
inline float rcp(float _X) restrict(amp);

 
inline double rcp(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 为其计算与倒数值。  
  
### <a name="return-value"></a>返回值  
 指定的自变量的倒数。  
  
##  <a name="reversebits"></a>  reversebits  
 _X 中位的顺序反转  
  
```  
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 无符号整数值  
  
### <a name="return-value"></a>返回值  
 以 _X 中位的反序的顺序返回值  
  
##  <a name="saturate"></a>  saturate  
 Clamps 的 0 到 1 范围内的 _X  
  
```  
inline float saturate(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回固定于 0 和 1 之间的 _X  
  
##  <a name="sign"></a>  sign  
 确定指定的自变量的符号。  
  
```  
inline int sign(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 整数值  
  
### <a name="return-value"></a>返回值  
 自变量的符号。  
  
##  <a name="smoothstep"></a>  smoothstep  
 如果 _X 处于范围 [_Min，_Max] 0 和 1 之间，返回平滑 Hermite 内插。  
  
```  
inline float smoothstep(
    float _Min,  
    float _Max,  
    float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_Min`  
 浮点值  
  
 `_Max`  
 浮点值  
  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 如果 _X 小于 _Min，则返回 0；如果 _X 大于 _Max，则返回 1；否则，如果 _X 处于范围 [_Min，_Max] 中，则返回 0 和 1 之间的值  
  
##  <a name="step"></a>  step  
 比较两个值，返回 0 或 1 基于的值大于  
  
```  
inline float step(
    float _Y,  
    float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_Y`  
 浮点值  
  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 如果 _X 大于或等于 _Y，则返回 1；否则返回 0  
  
##  <a name="umax"></a>  umax  
 确定自变量的最大数值  
  
```  
inline unsigned int umax(
    unsigned int _X,  
    unsigned int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 整数值  
  
 `_Y`  
 整数值  
  
### <a name="return-value"></a>返回值  
 返回自变量的最大数值  
  
##  <a name="umin"></a>  umin  
 确定自变量的最小数值  
  
```  
inline unsigned int umin(
    unsigned int _X,  
    unsigned int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 整数值  
  
 `_Y`  
 整数值  
  
### <a name="return-value"></a>返回值  
 返回自变量的最小数值  
  
## <a name="see-also"></a>另请参阅  
 [Concurrency::direct3d 命名空间](concurrency-direct3d-namespace.md)

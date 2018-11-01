---
title: Concurrency::direct3d 命名空间函数 (AMP)
ms.date: 08/31/2018
f1_keywords:
- amp/Concurrency::direct3d::abs
- amp/Concurrency::direct3d::countbits
- amp/Concurrency::direct3d::create_accelerator_view
- amp/Concurrency::direct3d::d3d_access_lock
- amp/Concurrency::direct3d::d3d_access_unlock
- amp/Concurrency::direct3d::firstbithigh
- amp/Concurrency::direct3d::get_buffer
- amp/Concurrency::direct3d::get_device
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
ms.assetid: 28943b62-52c9-42dc-baf1-ca7b095c1a19
ms.openlocfilehash: b721d19cd51a9eb1d07de8898b18728854decb4e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519726"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency::direct3d 命名空间函数 (AMP)

||||
|-|-|-|
|[abs](#abs)|[clamp](#clamp)|[countbits](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[firstbithigh](#firstbithigh)|
|[firstbitlow](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[imax](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[mad](#mad)|[make_array](#make_array)|[干扰](#noise)|
|[弧度为单位](#radians)|[rcp](#rcp)|[reversebits](#reversebits)|
|[saturate](#saturate)|[sign](#sign)|[smoothstep](#smoothstep)|
|[step](#step)|[umax](#umax)|[umin](#umin)|

## <a name="requirements"></a>要求

**标头：** amp.h **Namespace:** 并发

##  <a name="abs"></a>  abs

返回自变量的绝对值

```
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
整数值

### <a name="return-value"></a>返回值

返回自变量的绝对值。

##  <a name="clamp"></a>  clamp

计算限制到由第二个和第三个指定的参数定义的范围内的第一个指定参数的值。

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

*_X*<br/>
要被限制的值

*_Min*<br/>
限制范围的下限。

*_Max*<br/>
限制范围的上限。

### <a name="return-value"></a>返回值

限制的值`_X`。

##  <a name="countbits"></a>  countbits

计算 _X 中的设置位的数目

```
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
无符号整数值

### <a name="return-value"></a>返回值

返回 _X 中的设置位数

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

*_Accelerator*<br/>
新的 accelerator_view 是要创建快捷键。

*_D3D_device*<br/>
指向 Direct3D 设备接口的指针。

*_Disable_timeout*<br/>
一个布尔参数，指定是否应为新创建的 accelerator_view 禁用超时。 这对应于 Direct3D 设备创建的 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 标志，用于指示操作系统是否应允许采用多个 2 秒，而不必重置设备在每个 Windows 超时值执行的工作负荷检测和恢复机制。 如果您需要在 accelerator_view 上执行耗时任务，则建议使用此标志。

*_Qmode*<br/>
[Queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)要用于新创建的 accelerator_view。 此参数具有默认值为`queuing_mode_automatic`。

## <a name="return-value"></a>返回值

`accelerator_view`从传入的 Direct3D 设备接口创建的对象。

## <a name="remarks"></a>备注

此函数创建一个新`accelerator_view`从现有指针到 Direct3D 设备接口的对象。 如果函数调用成功，该参数的引用计数会递增通过`AddRef`对接口的调用。 不再需要在您的 DirectX 代码中时，可以安全地释放对象。 如果方法调用失败， [runtime_exception](runtime-exception-class.md)引发。

`accelerator_view`通过使用此函数创建的对象是线程安全。 你必须同步并发使用`accelerator_view`对象。 非同步并发使用的`accelerator_view`对象和原始 ID3D11Device 接口导致未定义的行为。

C + + AMP 运行时提供详细的错误信息在调试模式下使用 D3D 调试层，如果您使用`D3D11_CREATE_DEVICE_DEBUG`标志。

##  <a name="d3d_access_lock"></a>  d3d_access_lock

获取一个锁出于安全执行 D3D 操作在与 accelerator_view 共享的资源。 Accelerator_view 和所有与此 accelerator_view 内部关联的 c + + AMP 资源会采用此锁时执行的操作和其他线程占有 D3D 访问锁时，将阻止。 此锁为非递归： 它是未定义从已经持有锁的线程调用此函数的行为。 它是未定义的行为来执行操作的 accelerator_view 或任何与保留 D3D 访问锁的线程的 accelerator_view 相关联的数据容器。 也可参见 scoped_d3d_access_lock，基于范围的 D3D 访问锁的 RAII 样式类。

```
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>参数

*_Av*<br/>
要锁定的 accelerator_view。

##  <a name="d3d_access_try_lock"></a>  d3d_access_try_lock

尝试获取 accelerator_view 上的 D3D 访问锁而不会阻塞。

```
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>参数

*_Av*<br/>
要锁定的 accelerator_view。

### <a name="return-value"></a>返回值

如果已获取锁，则为 true 或 false，如果当前由另一个线程。

##  <a name="d3d_access_unlock"></a>  d3d_access_unlock

发布给定 accelerator_view 上的 D3D 访问锁。 如果调用线程不拥有 accelerator_view 上的锁结果不确定。

```
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>参数

*_Av*<br/>
将释放该锁的 accelerator_view。

##  <a name="firstbithigh"></a>  firstbithigh

获取 _X，开头为最高顺序位及位移至最低顺序位中的第一组位的位置。

```
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
整数值

### <a name="return-value"></a>返回值

第一组位的位置

##  <a name="firstbitlow"></a>  firstbitlow

获取 _X，从最低顺序位开始，从而最高顺序位中的第一组位的位置。

```
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
整数值

### <a name="return-value"></a>返回值

返回第一组位的位置

##  <a name="get_buffer"></a>  get_buffer

获取指定的数组的基础 Direct3D 缓冲区接口。

```
template<
    typename value_type,
    int _Rank
>
IUnknown *get_buffer(
    const array<value_type, _Rank>& _Array)  ;
```

### <a name="parameters"></a>参数

*value_type*<br/>
数组中元素的类型。

*_Rank*<br/>
数组的秩。

*_Array*<br/>
一个数组，为其返回基础 Direct3D 缓冲区接口 Direct3D accelerator_view 上。

### <a name="return-value"></a>返回值

对应于数组的基础 Direct3D 缓冲区 IUnknown 接口指针。

## <a name="a-namegetdevice-getdevice"></a><a name="get_device"> get_device

获取基础 accelerator_view D3D 设备接口。

```
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>参数

*Av*<br/>
为其返回基础 D3D 设备接口的 D3D accelerator_view。

### <a name="return-value"></a>返回值

`IUnknown`基础 accelerator_view D3D 设备的接口指针。

##  <a name="imax"></a>  imax

确定自变量的最大数值

```
inline int imax(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
整数值

*_Y*<br/>
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

*_X*<br/>
整数值

*_Y*<br/>
整数值

### <a name="return-value"></a>返回值

返回自变量的最小数值

##  <a name="is_timeout_disabled"></a>  is_timeout_disabled

返回一个布尔标志，指示是否针对 accelerator_view 禁用超时。 这对应于 Direct3D 设备创建的 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 标志。

```
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>参数

*_Accelerator_view*<br/>
超时禁用设置要为进行查询的 accelerator_view。

### <a name="return-value"></a>返回值

布尔标志，指示是否针对 accelerator_view 禁用超时。

##  <a name="mad"></a>  mad

计算第一个和第二个指定参数的产品，然后添加第三个指定的参数。

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

*_X*<br/>
指定的第一个参数。

*_Y*<br/>
第二个指定的参数。

*_Z*<br/>
第三个指定的参数。

### <a name="return-value"></a>返回值

结果`_X` \* `_Y`  +  `_Z`。

##  <a name="make_array"></a>  make_array

从 Direct3D 缓冲区接口指针创建一个数组。

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

*value_type*<br/>
要创建的数组元素类型。

*_Rank*<br/>
要创建的数组的秩。

*_Extent*<br/>
描述数组聚合形状的范围。

*_Rv*<br/>
数组是要创建 D3D 加速器视图。

*_D3D_buffer*<br/>
若要创建从数组的 D3D 缓冲区 IUnknown 接口指针。

### <a name="return-value"></a>返回值

创建使用提供的 Direct3D 缓冲区的数组。

##  <a name="noise"></a>  干扰

通过采用 Perlin 噪音算法生成一个随机值

```
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
从其生成 Perlin 噪音的浮点值

### <a name="return-value"></a>返回值

返回在一个介于 -1 和 1 之间的 Perlin 噪音值

##  <a name="radians"></a>  弧度为单位

将 _X 从度数转换为弧度

```
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回从度数转换到弧度的 _X。

##  <a name="rcp"></a>  rcp

通过使用快速近似计算指定参数的倒数。

```
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
要为其计算倒数值。

### <a name="return-value"></a>返回值

指定的参数的倒数。

##  <a name="reversebits"></a>  reversebits

颠倒 _X 中位的顺序

```
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
无符号整数值

### <a name="return-value"></a>返回值

以 _X 中位的反序的顺序返回值

##  <a name="saturate"></a>  saturate

将为 0 到 1 范围内的 _X 夹紧

```
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回固定于 0 和 1 之间的 _X

##  <a name="sign"></a>  登录

确定指定的参数的符号。

```
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
整数值

### <a name="return-value"></a>返回值

参数的符号。

##  <a name="smoothstep"></a>  smoothstep

如果 _X 处于范围 [_Min，_Max] 将返回介于 0 和 1 之间平滑的 Hermite 插值。

```
inline float smoothstep(
    float _Min,
    float _Max,
    float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_Min*<br/>
浮点值

*_Max*<br/>
浮点值

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

如果 _X 小于 _Min，则返回 0；如果 _X 大于 _Max，则返回 1；否则，如果 _X 处于范围 [_Min，_Max] 中，则返回 0 和 1 之间的值

##  <a name="step"></a>  步骤

比较两个值，返回 0 或 1 基于的值大于

```
inline float step(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_Y*<br/>
浮点值

*_X*<br/>
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

*_X*<br/>
整数值

*_Y*<br/>
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

*_X*<br/>
整数值

*_Y*<br/>
整数值

### <a name="return-value"></a>返回值

返回自变量的最小数值

## <a name="see-also"></a>请参阅

[Concurrency::direct3d 命名空间](concurrency-direct3d-namespace.md)

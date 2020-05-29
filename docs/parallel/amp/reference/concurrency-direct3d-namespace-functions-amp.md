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
ms.openlocfilehash: e21b1f2869ab81973b341abc5371714fbf8580e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375931"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency::direct3d 命名空间函数 (AMP)

||||
|-|-|-|
|[Abs](#abs)|[钳](#clamp)|[计数位](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[第一位高](#firstbithigh)|
|[第一比特洛](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[IMAX 巨幕](#imax)|[伊宁](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[疯狂](#mad)|[make_array](#make_array)|[噪声](#noise)|
|[弧度](#radians)|[rcp](#rcp)|[反向位](#reversebits)|
|[饱和](#saturate)|[标志](#sign)|[平滑步骤](#smoothstep)|
|[步](#step)|[乌马克斯](#umax)|[乌宁](#umin)|

## <a name="requirements"></a>要求

**标题：amp.h** **命名空间：** 并发性

## <a name="abs"></a><a name="abs"></a>Abs

返回参数的绝对值

```cpp
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
整数值

### <a name="return-value"></a>返回值

返回参数的绝对值。

## <a name="clamp"></a><a name="clamp"></a>钳

计算第一个指定参数的值，该参数夹紧在第二个和第三个指定参数定义的范围内。

```cpp
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
要夹紧的值

*_Min*<br/>
夹紧范围的下限。

*_Max*<br/>
夹紧范围的上限。

### <a name="return-value"></a>返回值

的夹紧值`_X`。

## <a name="countbits"></a><a name="countbits"></a>计数位

在_X中计算设置位数

```cpp
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
无符号整数值

### <a name="return-value"></a>返回值

返回_X中的设置位数

## <a name="create_accelerator_view"></a><a name="create_accelerator_view"></a>create_accelerator_view

从指向 Direct3D 设备接口的指针创建[accelerator_view](accelerator-view-class.md)对象。

## <a name="syntax"></a>语法

```cpp
accelerator_view create_accelerator_view(
    IUnknown * _D3D_device
    queuing_mode _Qmode = queuing_mode_automatic);

accelerator_view create_accelerator_view(
    accelerator& _Accelerator,
    bool _Disable_timeout
    queuing_mode _Qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>参数

*_Accelerator*<br/>
要创建新accelerator_view的加速器。

*_D3D_device*<br/>
指向 Direct3D 设备接口的指针。

*_Disable_timeout*<br/>
布尔参数，用于指定是否应为新创建的accelerator_view禁用超时。 这对应于 Direct3D 设备创建D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT标志，用于指示操作系统是否应允许执行超过 2 秒的工作负载，而无需根据 Windows 超时检测和恢复机制重置设备。 如果需要在accelerator_view执行耗时的任务，建议使用此标志。

*_Qmode*<br/>
用于[新](concurrency-namespace-enums-amp.md#queuing_mode)创建的accelerator_viewqueuing_mode。 此参数的默认值为`queuing_mode_automatic`。

## <a name="return-value"></a>返回值

从`accelerator_view`传递的 Direct3D 设备接口创建的对象。

## <a name="remarks"></a>备注

此函数从现有指针`accelerator_view`创建一个新对象到 Direct3D 设备接口。 如果函数调用成功，则参数的引用计数将通过使用对接口的`AddRef`调用增加。 当 DirectX 代码中不再需要对象时，可以安全地释放该对象。 如果方法调用失败，将引发[runtime_exception。](runtime-exception-class.md)

使用此`accelerator_view`函数创建的对象是线程安全。 必须同步`accelerator_view`对象的并发使用。 `accelerator_view`对象和原始 ID3D11Device 接口的未同步并发使用会导致未定义的行为。

如果使用`D3D11_CREATE_DEVICE_DEBUG`标志，C++ AMP 运行时通过使用 D3D 调试层在调试模式下提供详细的错误信息。

## <a name="d3d_access_lock"></a><a name="d3d_access_lock"></a>d3d_access_lock

获取accelerator_view上的锁，以便对与accelerator_view共享的资源安全地执行 D3D 操作。 执行操作时，accelerator_view和所有与此accelerator_view关联的所有C++ AMP 资源在内部获取此锁，并在另一个线程持有 D3D 访问锁时阻止。 此锁是非递归的：从已持有锁的线程调用此函数是未定义的行为。 从保存 D3D 访问锁的线程中对accelerator_view或任何与accelerator_view关联的数据容器执行操作是未定义的行为。 另请参阅scoped_d3d_access_lock，即基于作用域的 D3D 访问锁的 RAII 样式类。

```cpp
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>参数

*_Av*<br/>
要锁定accelerator_view。

## <a name="d3d_access_try_lock"></a><a name="d3d_access_try_lock"></a>d3d_access_try_lock

尝试在accelerator_view上获取 D3D 访问锁，而不会阻塞。

```cpp
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>参数

*_Av*<br/>
要锁定accelerator_view。

### <a name="return-value"></a>返回值

如果获取了锁，则为 true，如果锁当前由另一个线程持有，则为 false。

## <a name="d3d_access_unlock"></a><a name="d3d_access_unlock"></a>d3d_access_unlock

释放给定accelerator_view上的 D3D 访问锁。 如果调用线程未在accelerator_view上持有锁，则结果未定义。

```cpp
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>参数

*_Av*<br/>
要释放锁的accelerator_view。

## <a name="firstbithigh"></a><a name="firstbithigh"></a>第一位高

获取_X中第一个集位的位置，从最高阶位开始，然后向最低阶位移动。

```cpp
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
整数值

### <a name="return-value"></a>返回值

第一个设置位的位置

## <a name="firstbitlow"></a><a name="firstbitlow"></a>第一比特洛

获取_X中第一个设置位的位置，从最低阶位开始，然后朝着最高阶位工作。

```cpp
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
整数值

### <a name="return-value"></a>返回值

返回第一个设置位的位置

## <a name="get_buffer"></a><a name="get_buffer"></a>get_buffer

获取指定数组基础的 Direct3D 缓冲区接口。

```cpp
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
Direct3D 上的数组accelerator_view返回基础 Direct3D 缓冲区接口。

### <a name="return-value"></a>返回值

I未知接口指针对应于阵列基础的 Direct3D 缓冲区。

## <a name="a-nameget_device-get_device"></a><a name="get_device">get_device

获取accelerator_view基础的 D3D 设备接口。

```cpp
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>参数

*Av*<br/>
返回基础 D3D 设备接口的 D3D accelerator_view。

### <a name="return-value"></a>返回值

accelerator_view`IUnknown`基础的 D3D 设备的接口指针。

## <a name="imax"></a><a name="imax"></a>Imax

确定参数的最大数值

```cpp
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

返回参数的最大数值

## <a name="imin"></a><a name="imin"></a>伊宁

确定参数的最小数值

```cpp
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

返回参数的最小数值

## <a name="is_timeout_disabled"></a><a name="is_timeout_disabled"></a>is_timeout_disabled

返回一个布尔标志，指示指定accelerator_view是否禁用超时。 这对应于 Direct3D 设备创建的D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT标志。

```cpp
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>参数

*_Accelerator_view*<br/>
要查询已禁用超时设置accelerator_view。

### <a name="return-value"></a>返回值

一个布尔标志，指示指定accelerator_view是否禁用超时。

## <a name="mad"></a><a name="mad"></a>疯狂

计算第一个和第二个指定参数的积，然后添加第三个指定的参数。

```cpp
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
第一个指定的参数。

*_Y*<br/>
第二个指定的参数。

*_Z*<br/>
第三个指定的参数。

### <a name="return-value"></a>返回值

`_X``_Z`的结果。 \* `_Y`  + 

## <a name="make_array"></a><a name="make_array"></a>make_array

从 Direct3D 缓冲区接口指针创建数组。

```cpp
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
要创建的数组的元素类型。

*_Rank*<br/>
要创建的数组的排名。

*_Extent*<br/>
描述数组聚合形状的范围。

*_Rv*<br/>
要在其中创建阵列的 D3D 快捷键视图。

*_D3D_buffer*<br/>
D3D 缓冲区的 I 未知接口指针，用于从中创建数组。

### <a name="return-value"></a>返回值

使用提供的 Direct3D 缓冲区创建的数组。

## <a name="noise"></a><a name="noise"></a>噪声

通过采用 Perlin 噪音算法生成一个随机值

```cpp
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
从其生成 Perlin 噪音的浮点值

### <a name="return-value"></a>返回值

返回在一个介于 -1 和 1 之间的 Perlin 噪音值

## <a name="radians"></a><a name="radians"></a>弧度

将_X从度转换为弧度

```cpp
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回从度数转换到弧度的 _X。

## <a name="rcp"></a><a name="rcp"></a>Rcp

使用快速近似计算指定参数的对数。

```cpp
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
要计算对数的值。

### <a name="return-value"></a>返回值

指定参数的对等项。

## <a name="reversebits"></a><a name="reversebits"></a>反向位

反转_X位的顺序

```cpp
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
无符号整数值

### <a name="return-value"></a>返回值

以 _X 中位的反序的顺序返回值

## <a name="saturate"></a><a name="saturate"></a>饱和

夹钳_X 0 到 1 的范围内

```cpp
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回固定于 0 和 1 之间的 _X

## <a name="sign"></a><a name="sign"></a>标志

确定指定参数的符号。

```cpp
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
整数值

### <a name="return-value"></a>返回值

参数的标志。

## <a name="smoothstep"></a><a name="smoothstep"></a>平滑步骤

如果_X在 [_Min，_Max]范围内，则返回介于 0 和 1 之间的平滑 Hermite 插值。

```cpp
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

## <a name="step"></a><a name="step"></a>步

比较两个值，返回 0 或 1 基于哪个值较大

```cpp
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

## <a name="umax"></a><a name="umax"></a>乌马克斯

确定参数的最大数值

```cpp
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

返回参数的最大数值

## <a name="umin"></a><a name="umin"></a>乌宁

确定参数的最小数值

```cpp
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

返回参数的最小数值

## <a name="see-also"></a>另请参阅

[Concurrency::direct3d 命名空间](concurrency-direct3d-namespace.md)

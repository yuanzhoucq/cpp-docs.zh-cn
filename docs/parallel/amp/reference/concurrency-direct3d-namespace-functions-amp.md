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
ms.openlocfilehash: 438d211ac2f15bf781b704a7d0d7484d1542f131
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424979"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency::direct3d 命名空间函数 (AMP)

||||
|-|-|-|
|[abs](#abs)|[固定](#clamp)|[countbits](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[firstbithigh](#firstbithigh)|
|[firstbitlow](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[imax](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[mad](#mad)|[make_array](#make_array)|[点](#noise)|
|[π](#radians)|[rcp](#rcp)|[reversebits](#reversebits)|
|[饱和](#saturate)|[sign](#sign)|[smoothstep](#smoothstep)|
|[分步](#step)|[umax](#umax)|[umin](#umin)|

## <a name="requirements"></a>要求

**标头：** Amp**命名空间：** 并发

## <a name="abs"></a>abs

返回参数的绝对值。

```cpp
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>parameters

*_X*<br/>
整数值

### <a name="return-value"></a>返回值

返回参数的绝对值。

## <a name="clamp"></a>固定

将第一个指定参数限制的值计算为第二个和第三个指定参数所定义的范围。

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

### <a name="parameters"></a>parameters

*_X*<br/>
要限制的值

*_Min*<br/>
钳位范围的下限。

*_Max*<br/>
钳位范围的上限。

### <a name="return-value"></a>返回值

`_X`的限制值。

## <a name="countbits"></a>countbits

计算 _X 中设置的位数

```cpp
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>parameters

*_X*<br/>
无符号整数值

### <a name="return-value"></a>返回值

返回 _X 中设置的位数

## <a name="create_accelerator_view"></a>create_accelerator_view

从指向 Direct3D 设备接口的指针创建一个[accelerator_view](accelerator-view-class.md)对象。

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

### <a name="parameters"></a>parameters

*_Accelerator*<br/>
要在其上创建新 accelerator_view 的快捷键。

*_D3D_device*<br/>
指向 Direct3D 设备接口的指针。

*_Disable_timeout*<br/>
一个布尔参数，指定是否应为新创建的 accelerator_view 禁用超时。 这对应于 Direct3D 设备创建的 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 标志，用于指示操作系统是否应允许在不重置设备的情况下执行超过2秒的工作负荷检测和恢复机制。 如果需要对 accelerator_view 执行耗时的任务，建议使用此标志。

*_Qmode*<br/>
要用于新创建的 accelerator_view 的[queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) 。 此参数的默认值为 `queuing_mode_automatic`。

## <a name="return-value"></a>返回值

从通过的 Direct3D 设备接口创建的 `accelerator_view` 对象。

## <a name="remarks"></a>备注

此函数使用现有的指向 Direct3D 设备接口的指针创建新的 `accelerator_view` 对象。 如果函数调用成功，则通过对接口的 `AddRef` 调用来递增参数的引用计数。 当你的 DirectX 代码中不再需要该对象时，可以安全地释放它。 如果方法调用失败，则会引发[runtime_exception](runtime-exception-class.md) 。

使用此函数创建的 `accelerator_view` 对象是线程安全的。 必须同步 `accelerator_view` 对象的并发使用。 `accelerator_view` 对象的并发使用不同步，原始 ID3D11Device 接口会导致未定义的行为。

如果C++使用 `D3D11_CREATE_DEVICE_DEBUG` 标志，AMP 运行时将使用 D3D 调试层提供调试模式下的详细错误信息。

## <a name="d3d_access_lock"></a>d3d_access_lock

获取 accelerator_view 上的锁定，目的是为了在与 accelerator_view 共享的资源上安全执行 D3D 操作。 当执行操作时C++ ，与此 accelerator_view 关联的 accelerator_view 和所有 AMP 资源将在此锁定，并在另一个线程持有 D3D 访问锁定时被阻止。 此锁是非递归的：从已经持有锁的线程调用此函数是未定义的行为。 这是一种未定义的行为，用于对 accelerator_view 或与包含 D3D 访问锁定的线程中的 accelerator_view 相关联的任何数据容器执行操作。 另请参阅 scoped_d3d_access_lock，这是基于作用域的 D3D 访问锁的 RAII 样式类。

```cpp
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>parameters

*_Av*<br/>
要锁定的 accelerator_view。

## <a name="d3d_access_try_lock"></a>d3d_access_try_lock

尝试在不阻止的情况下获取 accelerator_view 上的 D3D 访问锁。

```cpp
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>parameters

*_Av*<br/>
要锁定的 accelerator_view。

### <a name="return-value"></a>返回值

如果已获取锁，则为 true; 否则为 false。

## <a name="d3d_access_unlock"></a>d3d_access_unlock

释放给定 accelerator_view 上的 D3D 访问锁。 如果调用线程未持有 accelerator_view 锁，则结果是不确定的。

```cpp
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>parameters

*_Av*<br/>
要为其释放锁的 accelerator_view。

## <a name="firstbithigh"></a>firstbithigh

获取 _X 中第一组位的位置，从最高序位开始，到最低顺序位。

```cpp
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>parameters

*_X*<br/>
整数值

### <a name="return-value"></a>返回值

第一组位的位置

## <a name="firstbitlow"></a>firstbitlow

获取 _X 中第一组位的位置，以最低顺序位开始，并向最高序位工作。

```cpp
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>parameters

*_X*<br/>
整数值

### <a name="return-value"></a>返回值

返回第一组位的位置

## <a name="get_buffer"></a>get_buffer

获取指定数组基础的 Direct3D 缓冲区接口。

```cpp
template<
    typename value_type,
    int _Rank
>
IUnknown *get_buffer(
    const array<value_type, _Rank>& _Array)  ;
```

### <a name="parameters"></a>parameters

*value_type*<br/>
数组中元素的类型。

*_Rank*<br/>
数组的秩。

*_Array*<br/>
Direct3D accelerator_view 上的一个数组，将为其返回基础 Direct3D 缓冲区接口。

### <a name="return-value"></a>返回值

与数组基础的 Direct3D 缓冲区对应的 IUnknown 接口指针。

## <a name="a-nameget_device-get_device"></a><a name="get_device"> get_device

获取 accelerator_view 基础的 D3D 设备接口。

```cpp
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>parameters

*Av*<br/>
为其返回基础 D3D 设备接口的 D3D accelerator_view。

### <a name="return-value"></a>返回值

Accelerator_view 的基础 D3D 设备的 `IUnknown` 接口指针。

## <a name="imax"></a>imax

确定参数的最大数值

```cpp
inline int imax(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>parameters

*_X*<br/>
整数值

*_Y*<br/>
整数值

### <a name="return-value"></a>返回值

返回参数的最大数值

## <a name="imin"></a>imin

确定参数的最小数值

```cpp
inline int imin(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>parameters

*_X*<br/>
整数值

*_Y*<br/>
整数值

### <a name="return-value"></a>返回值

返回参数的最小数值

## <a name="is_timeout_disabled"></a>is_timeout_disabled

返回一个布尔标志，指示是否为指定的 accelerator_view 禁用超时。 这对应于 Direct3D 设备创建的 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 标志。

```cpp
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>parameters

*_Accelerator_view*<br/>
要查询其超时禁用设置的 accelerator_view。

### <a name="return-value"></a>返回值

布尔标志，指示是否为指定的 accelerator_view 禁用超时。

## <a name="mad"></a>mad

计算第一个和第二个指定参数的乘积，然后添加第三个指定的参数。

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

### <a name="parameters"></a>parameters

*_X*<br/>
第一个指定的参数。

*_Y*<br/>
第二个指定的参数。

*_Z*<br/>
第三个指定的参数。

### <a name="return-value"></a>返回值

`_X` \* `_Y` + `_Z`的结果。

## <a name="make_array"></a>make_array

从 Direct3D 缓冲区接口指针创建一个数组。

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

### <a name="parameters"></a>parameters

*value_type*<br/>
要创建的数组的元素类型。

*_Rank*<br/>
要创建的数组的秩。

*_Extent*<br/>
描述数组聚合的形状的范围。

*_Rv*<br/>
要在其上创建数组的 D3D 加速器视图。

*_D3D_buffer*<br/>
要从中创建数组的 D3D 缓冲区的 IUnknown 接口指针。

### <a name="return-value"></a>返回值

使用提供的 Direct3D 缓冲区创建的数组。

## <a name="noise"></a>点

通过采用 Perlin 噪音算法生成一个随机值

```cpp
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>parameters

*_X*<br/>
从其生成 Perlin 噪音的浮点值

### <a name="return-value"></a>返回值

返回在一个介于 -1 和 1 之间的 Perlin 噪音值

## <a name="radians"></a>π

将 _X 从度转换为弧度

```cpp
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>parameters

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回从度数转换到弧度的 _X。

## <a name="rcp"></a>rcp

使用快速近似计算指定参数的倒数。

```cpp
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>parameters

*_X*<br/>
要为其计算倒数的值。

### <a name="return-value"></a>返回值

指定参数的倒数。

## <a name="reversebits"></a>reversebits

反转 _X 中位的顺序

```cpp
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>parameters

*_X*<br/>
无符号整数值

### <a name="return-value"></a>返回值

以 _X 中位的反序的顺序返回值

## <a name="saturate"></a>饱和

夹紧在0到1范围内 _X

```cpp
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>parameters

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回固定于 0 和 1 之间的 _X

## <a name="sign"></a>表明

确定指定参数的符号。

```cpp
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>parameters

*_X*<br/>
整数值

### <a name="return-value"></a>返回值

参数的符号。

## <a name="smoothstep"></a>smoothstep

如果 _X 在 [_Min，_Max] 范围内，则返回介于0和1之间的平滑 Hermite 内插。

```cpp
inline float smoothstep(
    float _Min,
    float _Max,
    float _X) restrict(amp);
```

### <a name="parameters"></a>parameters

*_Min*<br/>
浮点值

*_Max*<br/>
浮点值

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

如果 _X 小于 _Min，则返回 0；如果 _X 大于 _Max，则返回 1；否则，如果 _X 处于范围 [_Min，_Max] 中，则返回 0 和 1 之间的值

## <a name="step"></a>分步

比较两个值，根据哪个值更大返回0或1

```cpp
inline float step(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>parameters

*_Y*<br/>
浮点值

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

如果 _X 大于或等于 _Y，则返回 1；否则返回 0

## <a name="umax"></a>umax

确定参数的最大数值

```cpp
inline unsigned int umax(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```

### <a name="parameters"></a>parameters

*_X*<br/>
整数值

*_Y*<br/>
整数值

### <a name="return-value"></a>返回值

返回参数的最大数值

## <a name="umin"></a>umin

确定参数的最小数值

```cpp
inline unsigned int umin(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```

### <a name="parameters"></a>parameters

*_X*<br/>
整数值

*_Y*<br/>
整数值

### <a name="return-value"></a>返回值

返回参数的最小数值

## <a name="see-also"></a>另请参阅

[Concurrency::direct3d 命名空间](concurrency-direct3d-namespace.md)

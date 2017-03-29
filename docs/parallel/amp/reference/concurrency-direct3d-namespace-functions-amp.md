---
title: "Concurrency:: direct3d 命名空间函数 (AMP) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: ad00006c9ab4f25887cf28ed5b977551c35bda9e
ms.lasthandoff: 03/17/2017

---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency:: direct3d 命名空间函数 (AMP)
||||  
|-|-|-|  
|[abs](#abs)|[clamp](#clamp)|[countbits](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|||
|[d3d_access_lock](#d3d_access_lock)|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|  
|[firstbithigh](#firstbithigh)|[firstbitlow](#firstbitlow)|[get_buffer](#get_buffer)|  
|[imax](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|  
|[mad](#mad)|[make_array](#make_array)|[噪音](#noise)|  
|[弧度为单位](#radians)|[rcp](#rcp)|[reversebits](#reversebits)|  
|[充斥着](#saturate)|[登录](#sign)|[smoothstep](#smoothstep)|  
|[步骤](#step)|[umax](#umax)|[umin](#umin)|  

## <a name="requirements"></a>要求
**标头︰** amp.h **Namespace:**并发
  
##  <a name="abs"></a>  abs  
 返回参数的绝对值  
  
```  
inline int abs(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 整数值  
  
### <a name="return-value"></a>返回值  
 返回参数的绝对值。  
  
##  <a name="clamp"></a>clamp  
 计算其限制为通过第二个和第三个指定的参数定义的范围的第一个指定参数的值。  
  
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
  
##  <a name="countbits"></a>countbits  
 计算 _X 中设置位的数目  
  
```  
inline unsigned int countbits(unsigned int _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 无符号整数值  
  
### <a name="return-value"></a>返回值  
 以 _X 中返回集比特数  

## <a name="create_accelerator_view"></a>create_accelerator_view  
创建[accelerator_view](accelerator-view-class.md)对象从一个指针，到 Direct3D 设备接口。  
  
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
 新 accelerator_view 是要创建加速器。  
  
 `_D3D_device`  
 指向 Direct3D 设备接口的指针。  
  
 `_Disable_timeout`  
 一个布尔参数，指定是否应为新创建的 accelerator_view 禁用超时。 这对应于用于创建 Direct3D 设备的 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 标志，用于指示操作系统应允许花费 2 秒以上的时间执行，而每个 Windows 超时检测和恢复机制将设备重置的工作负荷。 如果您需要在 accelerator_view 上执行耗时的任务，则建议使用此标志。  
  
 `_Qmode`  
 [Queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)要用于新创建的 accelerator_view。 此参数具有默认值为`queuing_mode_automatic`。  
  
## <a name="return-value"></a>返回值  
 `accelerator_view`从传入的 Direct3D 设备接口创建对象。  
  
## <a name="remarks"></a>备注  
 此函数创建一个新`accelerator_view`对象从现有的指针到 Direct3D 设备接口。 如果函数调用成功，该参数的引用计数会递增通过`AddRef`调用界面。 不再需要在 DirectX 代码中时，你可以安全地释放该对象。 如果方法调用失败， [runtime_exception](runtime-exception-class.md)引发。  
  
 `accelerator_view`通过使用此函数创建的对象是线程安全。 您必须同步的同时使用`accelerator_view`对象。 未同步的并发使用`accelerator_view`对象和原始 ID3D11Device 接口则会导致未定义的行为。  
  
 C + + AMP 运行时提供详细的错误信息，在调试模式下使用 D3D 调试层，如果您使用`D3D11_CREATE_DEVICE_DEBUG`标志。  
  
  
##  <a name="d3d_access_lock"></a>d3d_access_lock  
 获取用于安全地执行与 accelerator_view 共享资源上的 D3D 操作 accelerator_view 上的锁。 Accelerator_view 及其内部与此 accelerator_view 相关联的所有 c + + AMP 资源执行操作时需要此锁，而另一个线程持有 D3D 访问锁将阻止。 此锁不是递归的︰ 它是未定义的行为，以便从已持有锁的线程调用此函数。 它是未定义的行为在 accelerator_view 或与从持有 D3D 访问锁的线程 accelerator_view 相关联的任何数据容器上执行操作。 另请参阅 scoped_d3d_access_lock，为基于作用域的 D3D 访问锁定的 RAII 样式类。  
  
```  
void __cdecl d3d_access_lock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>参数  
 `_Av`  
 若要锁定 accelerator_view。  
  
##  <a name="d3d_access_try_lock"></a>d3d_access_try_lock  
 尝试获取对 accelerator_view 的 D3D 访问锁定而无需阻止。  
  
```  
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>参数  
 `_Av`  
 若要锁定 accelerator_view。  
  
### <a name="return-value"></a>返回值  
 如果已获取锁，则为 true 或 false，如果当前由另一个线程。  
  
##  <a name="d3d_access_unlock"></a>d3d_access_unlock  
 解锁 D3D 访问给定的 accelerator_view 上。 如果调用线程 accelerator_view 不保持锁定，结果不确定。  
  
```  
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>参数  
 `_Av`  
 Accelerator_view 将要释放锁。  
  
##  <a name="firstbithigh"></a>firstbithigh  
 获取 _X，从最高顺序位开始，然后转向最低顺序位中的第一个设置位的位置。  
  
```  
inline int firstbithigh(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 整数值  
  
### <a name="return-value"></a>返回值  
 第一个设置位的位置  
  
##  <a name="firstbitlow"></a>firstbitlow  
 获取 _X，开头的最低顺序位并努力的方向的高顺序位中的第一个设置位的位置。  
  
```  
inline int firstbitlow(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 整数值  
  
### <a name="return-value"></a>返回值  
 返回第一个设置位的位置  
  
##  <a name="get_buffer"></a>get_buffer  
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
  
##  <a name="imax"></a>imax  
 确定参数的最大数值  
  
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
 返回参数的最大数值  
  
##  <a name="imin"></a>imin  
 确定参数的最小数值  
  
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
 返回参数的最小数值  
  
##  <a name="is_timeout_disabled"></a>is_timeout_disabled  
 返回一个布尔型标志，指示是否对指定 accelerator_view 禁用超时。 这对应于用于创建 Direct3D 设备的 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 标志。  
  
```  
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```  
  
### <a name="parameters"></a>参数  
 `_Accelerator_view`  
 超时值对其禁用设置 accelerator_view 是进行查询。  
  
### <a name="return-value"></a>返回值  
 一个布尔型标志，该值指示是否对指定 accelerator_view 禁用超时。  
  
##  <a name="mad"></a>mad  
 计算的积的第一个和第二个指定的参数，然后添加第三个指定的参数。  
  
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
 指定的第一个参数。  
  
 `_Y`  
 第二个指定的参数。  
  
 `_Z`  
 第三个指定的参数。  
  
### <a name="return-value"></a>返回值  
 The result of `_X` * `_Y` + `_Z`.  
  
##  <a name="make_array"></a>make_array  
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
 要创建的数组的元素类型。  
  
 `_Rank`  
 要创建的数组的秩。  
  
 `_Extent`  
 一个描述数组聚合的形状的范围。  
  
 `_Rv`  
 该数组是要创建 D3D 快捷键视图。  
  
 `_D3D_buffer`  
 若要创建从数组的 D3D 缓冲区的 IUnknown 接口指针。  
  
### <a name="return-value"></a>返回值  
 创建使用提供的 Direct3D 缓冲区的数组。  
  
##  <a name="noise"></a>噪音  
 通过采用 Perlin 噪音算法生成一个随机值  
  
```  
inline float noise(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 从其生成 Perlin 噪音的浮点值  
  
### <a name="return-value"></a>返回值  
 返回在一个介于 -1 和 1 之间的 Perlin 噪音值  
  
##  <a name="radians"></a>弧度为单位  
 将 _X 从度数转换成弧度  
  
```  
inline float radians(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回从度数转换到弧度的 _X。  
  
##  <a name="rcp"></a>rcp  
 通过使用快速近似计算的指定参数的倒数。  
  
```  
inline float rcp(float _X) restrict(amp);

 
inline double rcp(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 为其计算与倒数的值。  
  
### <a name="return-value"></a>返回值  
 指定的参数的倒数。  
  
##  <a name="reversebits"></a>reversebits  
 _X 中位的顺序反转  
  
```  
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 无符号整数值  
  
### <a name="return-value"></a>返回值  
 以 _X 中位的反序的顺序返回值  
  
##  <a name="saturate"></a>saturate  
 Clamps 的 0 到 1 范围内的 _X  
  
```  
inline float saturate(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回固定于 0 和 1 之间的 _X  
  
##  <a name="sign"></a>登录  
 确定指定的参数符号。  
  
```  
inline int sign(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 整数值  
  
### <a name="return-value"></a>返回值  
 参数的符号。  
  
##  <a name="smoothstep"></a>smoothstep  
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
  
##  <a name="step"></a>步骤  
 比较两个值，返回 0 或 1 根据哪个值为更高版本  
  
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
  
##  <a name="umax"></a>umax  
 确定参数的最大数值  
  
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
 返回参数的最大数值  
  
##  <a name="umin"></a>umin  
 确定参数的最小数值  
  
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
 返回参数的最小数值  
  
## <a name="see-also"></a>另请参阅  
 [Concurrency::direct3d 命名空间](concurrency-direct3d-namespace.md)


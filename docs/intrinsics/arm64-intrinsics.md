---
title: ARM64 内部函数
description: Microsoft C++编译器支持的 ARM64 内部函数的列表。
f1_keywords:
- __break
- __addx18byte
- __addx18word
- __addx18dword
- __addx18qword
- __cas8
- __cas16
- __cas32
- __cas64
- __casa8
- __casa16
- __casa32
- __casa64
- __casl8
- __casl16
- __casl32
- __casl64
- __casal8
- __casal16
- __casal32
- __casal64
- __crc32b
- __crc32h
- __crc32w
- __crc32d
- __crc32cb
- __crc32ch
- __crc32cw
- __crc32cd
- __getReg
- __getRegFp
- __getCallerReg
- __getCallerRegFp
- __hlt
- __incx18byte
- __incx18word
- __incx18dword
- __incx18qword
- __ldar8
- __ldar16
- __ldar32
- __ldar64
- __ldapr8
- __ldapr16
- __ldapr32
- __ldapr64
- __prefetch2
- __readx18byte
- __readx18word
- __readx18dword
- __readx18qword
- __setReg
- __setRegFp
- __setCallerReg
- __setCallerRegFp
- __stlr8
- __stlr16
- __stlr32
- __stlr64
- __swp8
- __swp16
- __swp32
- __swp64
- __swpa8
- __swpa16
- __swpa32
- __swpa64
- __swpl8
- __swpl16
- __swpl32
- __swpl64
- __swpal8
- __swpal16
- __swpal32
- __swpal64
- __sys
- __svc
- __writex18byte
- __writex18word
- __writex18dword
- __writex18qword
author: sigatrev
ms.author: magardn
ms.date: 11/14/2019
ms.openlocfilehash: 196518439445824ddf5a7a841b30eb816251ba60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368207"
---
# <a name="arm64-intrinsics"></a>ARM64 内部函数

Microsoft C++编译器 （MSVC） 在 ARM64 体系结构上提供了以下内部函数。 有关 ARM 的详细信息，请参阅[ARM 开发人员文档](https://developer.arm.com/docs)网站的体系结构和软件开发工具部分。

## <a name="neon"></a><a name="top"></a>霓虹灯

ARM64 的 NEON 矢量指令集扩展提供单指令多数据 （SIMD） 功能。 它们类似于 MMX 和 SSE 矢量指令集中中 x86 和 x64 体系结构处理器中常见的指令集。

NEON 内部函数受支持，如标头文件*arm64_neon.h*中提供。 对 NEON 内部函数的 MSVC 支持类似于 ARM64 编译器的支持，该编译器记录在 ARM 信息中心网站上的[ARM NEON 内部参考](https://static.docs.arm.com/ihi0073/c/IHI0073C_arm_neon_intrinsics_ref.pdf)中。

## <a name="arm64-specific-intrinsics-listing"></a><a name="A"></a>ARM64 特定内部函数列表

|函数名称|指令|函数原型|
|-------------------|-----------------|------------------------|
|__break|BRK|空__break（int）|
|__addx18byte||无效__addx18byte（无符号长，无符号字符）|
|__addx18word||无效__addx18word（无符号长，无符号短）|
|__addx18dword||无效__addx18dword（无符号长，无符号长）|
|__addx18qword||无效__addx18qword（无符号长，无符号__int64）|
|__cas8|CASB|未签名__int8__cas8（未签名__int8易失性* _Target、未签名__int8_Comp、未签名__int8_Value）|
|__cas16|现金|无符号__int16__cas16（无符号__int16易失性* _Target，无符号__int16_Comp，未签名__int16_Value）|
|__cas32|CAS|无符号__int32__cas32（无符号__int32易失_Target、无符号__int32_Comp、无符号__int32_Value）|
|__cas64|CAS|未签名__int64__cas64（无符号__int64易失性* _Target、无符号__int64_Comp、无符号__int64_Value）|
|__casa8|CASAB|无符号__int8__casa8（无符号__int8易失性* _Target、无符号__int8_Comp、无符号__int8_Value）|
|__casa16|CASAH|未签名__int16__casa16（无符号__int16易失性* _Target、未签名__int16_Comp、未签名__int16_Value）|
|__casa32|CASA|未签名__int32__casa32（无符号__int32易失性* _Target、无符号__int32_Comp、无符号__int32_Value）|
|__casa64|CASA|未签名__int64__casa64（无符号__int64易失性* _Target、未签名__int64_Comp、无符号__int64_Value）|
|__casl8|CASLB|无符号__int8__casl8（无符号__int8易失性* _Target，未签名__int8_Comp，无符号__int8_Value）|
|__casl16|CASLH|未签名__int16__casl16（无符号__int16易失性* _Target、未签名__int16_Comp、未签名__int16_Value）|
|__casl32|CASL|未签名__int32__casl32（无符号__int32易失性* _Target、未签名__int32_Comp、无符号__int32_Value）|
|__casl64|CASL|未签名__int64__casl64（无符号__int64易失性* _Target、未签名__int64_Comp、无符号__int64_Value）|
|__casal8|卡萨布|未签名__int8__casal8（无符号__int8易失性* _Target、未签名__int8_Comp、无符号__int8_Value）|
|__casal16|卡萨勒|未签名__int16__casal16（无符号__int16易失性* _Target、未签名__int16_Comp、无符号__int16_Value）|
|__casal32|卡萨拉尔|未签名__int32__casal32（无符号__int32易失性* _Target，未签名__int32_Comp，无符号__int32_Value）|
|__casal64|卡萨拉尔|未签名__int64__casal64（无符号__int64易失性* _Target、无符号__int64_Comp、无符号__int64_Value）|
|__crc32b|CRC32B|未签名__int32__crc32b（未签名__int32，无符号__int32）|
|__crc32h|CRC32H|未签名__int32__crc32h（未签名__int32，无符号__int32）|
|__crc32w|CRC32W|未签名__int32__crc32w（无符号__int32，无符号__int32）|
|__crc32d|CRC32X|未签名__int32__crc32d（未签名__int32，无符号__int64）|
|__crc32cb|CRC32CB|未签名__int32__crc32cb（未签名__int32，无符号__int32）|
|__crc32ch|CRC32CH|未签名__int32__crc32ch（未签名__int32，未签名__int32）|
|__crc32cw|CRC32CW|未签名__int32__crc32cw（无符号__int32，无符号__int32）|
|__crc32cd|CRC32CX|未签名__int32__crc32cd（未签名__int32，未签名__int64）|
|__dmb|DMB|void __dmb(unsigned int `_Type`)<br /><br /> 将一个内存屏障操作插入指令流中。 参数 `_Type` 指定屏障强制执行的限制类型。<br /><br /> 有关可强制执行的限制类型的详细信息，请参阅[内存障碍限制](#BarrierRestrictions)。|
|__dsb|DSB|void __dsb(unsigned int _Type)<br /><br /> 将一个内存屏障操作插入指令流中。 参数 `_Type` 指定屏障强制执行的限制类型。<br /><br /> 有关可强制执行的限制类型的详细信息，请参阅[内存障碍限制](#BarrierRestrictions)。|
|__isb|ISB|void __isb(unsigned int _Type)<br /><br /> 将一个内存屏障操作插入指令流中。 参数 `_Type` 指定屏障强制执行的限制类型。<br /><br /> 有关可强制执行的限制类型的详细信息，请参阅[内存障碍限制](#BarrierRestrictions)。|
|__getReg||未签名__int64__getReg（int）|
|__getRegFp||双__getRegFp（int）|
|__getCallerReg||未签名__int64__getCallerReg（int）|
|__getCallerRegFp||双__getCallerRegFp（int）|
|__hvc|HVC|unsigned int __hvc(unsigned int, ...)|
|__hlt|HLT|int __hlt（无符号 int，...）|
|__incx18byte||无效__incx18byte（无符号长）|
|__incx18word||无效__incx18word（无符号长）|
|__incx18dword||无效__incx18dword（无符号长）|
|__incx18qword||空__incx18qword（无符号长）|
|__iso_volatile_load16||__int16_iso_volatile_load16（\_波动\__int16） \*<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/存储内部函数](#IsoVolatileLoadStore)。|
|__iso_volatile_load32||__int32_iso_volatile_load32（\_波动\__int32） \*<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/存储内部函数](#IsoVolatileLoadStore)。|
|__iso_volatile_load64||__int64_iso_volatile_load64（\_波动\__int64） \*<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/存储内部函数](#IsoVolatileLoadStore)。|
|__iso_volatile_load8||__int8_iso_volatile_load8（\_波动\__int8） \*<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/存储内部函数](#IsoVolatileLoadStore)。|
|__iso_volatile_store16||空__iso_volatile_store16（易\_挥\*_int16，_int16） \_<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/存储内部函数](#IsoVolatileLoadStore)。|
|__iso_volatile_store32||空__iso_volatile_store32（易\_\*挥_int32_int32） \_<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/存储内部函数](#IsoVolatileLoadStore)。|
|__iso_volatile_store64||空__iso_volatile_store64（易\_\*挥_int64，_int64） \_<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/存储内部函数](#IsoVolatileLoadStore)。|
|__iso_volatile_store8||空__iso_volatile_store8（挥\_发\*性\__int8，_int8）<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/存储内部函数](#IsoVolatileLoadStore)。|
|__ldar8|LDARB|未签名__int8__ldar8（未签名__int8易失性* _Target）|
|__ldar16|LDARH|无符号__int16__ldar16（无符号__int16易失性* _Target）|
|__ldar32|LDAR|未签名__int32__ldar32（未签名__int32易失性* _Target）|
|__ldar64|LDAR|未签名__int64__ldar64（未签名__int64易失性* _Target）|
|__ldapr8|LDAPRB|未签名__int8__ldapr8（未签名__int8易失性* _Target）|
|__ldapr16|LDAPRH|无符号__int16__ldapr16（无符号__int16易失性* _Target）|
|__ldapr32|LDAPR|未签名__int32__ldapr32（未签名__int32易失性* _Target）|
|__ldapr64|LDAPR|未签名__int64__ldapr64（无符号__int64易失性* _Target）|
|__mulh||\__int64__mulh（_int64、_int64）\_ \_|
|__prefetch|PRFM|_prefetch__cdecl\_空（空白\*）<br /><br /> 向`PRFM`系统提供内存提示，其中预取`PLDL1KEEP`操作表明，可能很快就会访问指定地址或附近的内存。 某些系统可能会选择优化此内存访问模式以提高运行时性能。 但是，从 c + + 语言的角度来看，此功能没有明显的影响，可能不执行任何操作。|
|__prefetch2|PRFM|空__cdecl_prefetch（\_空白\*，uint8_t普）<br /><br /> 向`PRFM`系统提供具有提供的预取操作的内存提示，以便很快可以访问指定地址或附近的内存。 某些系统可能会选择优化此内存访问模式以提高运行时性能。 但是，从 c + + 语言的角度来看，此功能没有明显的影响，可能不执行任何操作。|
|__readx18byte||无符号字符__readx18byte（未签名长）|
|__readx18word||无符号短__readx18word（无符号长）|
|__readx18dword||无符号长__readx18dword（无符号长）|
|__readx18qword||未签名__int64__readx18qword（无符号长）|
|__setReg||无效__setReg（无符号__int64）|
|__setRegFp||空__setRegFp（int，双）|
|__setCallerReg||无效__setCallerReg（无符号__int64）|
|__setCallerRegFp||空__setCallerRegFp（int，双）|
|__sev|SEV|void __sev(void)|
|__static_assert||空__static_assert（int，const \*char）|
|__stlr8|STLRB|无效__stlr8（无符号__int8易失性* _Target，无符号__int8_Value）|
|__stlr16|STLRH|无效__stlr16（无符号__int16易失性* _Target，无符号__int16_Value）|
|__stlr32|STLR|无效__stlr32（无符号__int32易失性* _Target，无符号__int32_Value）|
|__stlr64|STLR|无效__stlr64（无符号__int64易失性* _Target，无符号__int64_Value）|
|__swp8|SWPB|未签名__int8__swp8（无符号__int8易失性* _Target，无符号__int8_Value）|
|__swp16|SWPH|未签名__int16__swp16（未签名__int16易失性* _Target，无符号__int16_Value）|
|__swp32|SWP|无符号__int32__swp32（无符号__int32易失性* _Target，无符号__int32_Value）|
|__swp64|SWP|未签名__int64__swp64（无符号__int64易失性* _Target，无符号__int64_Value）|
|__swpa8|SWPAB|未签名__int8__swpa8（无符号__int8易失性* _Target，无符号__int8_Value）|
|__swpa16|SWPAH|未签名__int16__swpa16（无符号__int16易失性* _Target，无符号__int16_Value）|
|__swpa32|SWPA|未签名__int32__swpa32（无符号__int32易失性* _Target，无符号__int32_Value）|
|__swpa64|SWPA|无符号__int64__swpa64（无符号__int64易失性* _Target，无符号__int64_Value）|
|__swpl8|SWPLB|无符号__int8__swpl8（无符号__int8易失性* _Target，无符号__int8_Value）|
|__swpl16|SWPLH|未签名__int16__swpl16（无符号__int16易失性* _Target，无符号__int16_Value）|
|__swpl32|SWPL|未签名__int32__swpl32（无符号__int32易失性* _Target，无符号__int32_Value）|
|__swpl64|SWPL|无符号__int64__swpl64（无符号__int64易失性* _Target，无符号__int64_Value）|
|__swpal8|SWPALB|无符号__int8__swpal8（无符号__int8易失性* _Target，无符号__int8_Value）|
|__swpal16|SWPALH|未签名__int16__swpal16（无符号__int16易失性* _Target，无符号__int16_Value）|
|__swpal32|SWPAL|未签名__int32__swpal32（无符号__int32易失性* _Target，无符号__int32_Value）|
|__swpal64|SWPAL|无符号__int64__swpal64（无符号__int64易失性* _Target，无符号__int64_Value）|
|__sys|SYS|无符号__sys（int，__int64）|
|__svc|SVC|无符号的int__svc（无符号int，...）|
|__wfe|WFE|void __wfe(void)|
|__wfi|WFI|void __wfi(void)|
|__writex18byte||无效__writex18byte（无符号长，无符号字符）|
|__writex18word||无效__writex18word（无符号长，无符号短）|
|__writex18dword||无效__writex18dword（无符号长，无符号长）|
|__writex18qword||无效__writex18qword（无符号长，无符号__int64）|
|__umulh||未签名\__int64__umulh（未签名\__int64，未签名\__int64）|
|_CopyDoubleFromInt64||双_CopyDoubleFromInt64（_int64）\_|
|_CopyFloatFromInt32||浮_CopyFloatFromInt32（_int32）\_|
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat(float)|
|_CopyInt64FromDouble||__int64 _CopyInt64FromDouble(double)|
|_CountLeadingOnes||unsigned int _CountLeadingOnes(unsigned long)|
|_CountLeadingOnes64||无符号_CountLeadingOnes64（无符号\__int64）|
|_CountLeadingSigns||unsigned int _CountLeadingSigns(long)|
|_CountLeadingSigns64||无符号_CountLeadingSigns64（_int64）\_|
|_CountLeadingZeros||unsigned int _CountLeadingZeros(unsigned long)|
|_CountLeadingZeros64||无符号的int_CountLeadingZeros64（无\_符号_int64）|
|_ReadStatusReg|MRS|\__int64_ReadStatusReg（国际）|
|_WriteStatusReg|MSR|空_WriteStatusReg（因，_int64） \_|

[[返回顶部](#top)]

### <a name="memory-barrier-restrictions"></a><a name="BarrierRestrictions"></a>内存障碍限制

内部函数`__dmb`（数据内存屏障）、（`__dsb`数据同步屏障）和`__isb`（指令同步障碍）使用以下预定义值在共享域和受操作影响的访问类型方面指定内存障碍限制。

|限制值|说明|
|-----------------------|-----------------|
|_ARM64_BARRIER_SY|完整系统，读取和写入操作。|
|_ARM64_BARRIER_ST|完整系统，只写操作。|
|_ARM64_BARRIER_LD|完整系统，只读。|
|_ARM64_BARRIER_ISH|内部可共享，读取和写入操作。|
|_ARM64_BARRIER_ISHST|内部可共享，只写操作。|
|_ARM64_BARRIER_ISHLD|内部可共享，只读。|
|_ARM64_BARRIER_NSH|不可共享，读取和写入操作。|
|_ARM64_BARRIER_NSHST|不可共享，只写操作。|
|_ARM64_BARRIER_NSHLD|不可共享，只读。|
|_ARM64_BARRIER_OSH|外部可共享，读取和写入操作。|
|_ARM64_BARRIER_OSHST|外部可共享，只写操作。|
|_ARM64_BARRIER_OSHLD|外可共享，只读。|

对于`__isb`内部，当前唯一有效的限制是_ARM64_BARRIER_SY;所有其他值由体系结构保留。

### <a name="__iso_volatile_loadstore-intrinsics"></a><a name="IsoVolatileLoadStore"></a>__iso_volatile_load/存储内部

这些内部函数显式执行不受编译器优化约束的负载和存储。

```C
__int16 __iso_volatile_load16(const volatile __int16 * Location);
__int32 __iso_volatile_load32(const volatile __int32 * Location);
__int64 __iso_volatile_load64(const volatile __int64 * Location);
__int8 __iso_volatile_load8(const volatile __int8 * Location);

void __iso_volatile_store16(volatile __int16 * Location, __int16 Value);
void __iso_volatile_store32(volatile __int32 * Location, __int32 Value);
void __iso_volatile_store64(volatile __int64 * Location, __int64 Value);
void __iso_volatile_store8(volatile __int8 * Location, __int8 Value);
```

#### <a name="parameters"></a>参数

*位置*\
要从中读取或为其写入的内存位置的地址。

*价值*\
要写入指定内存位置的值（仅存储内部函数）。

#### <a name="return-value-load-intrinsics-only"></a>返回值（仅加载内部函数）

由*位置*指定的内存位置的值。

#### <a name="remarks"></a>备注

可以使用 和`__iso_volatile_load8/16/32/64``__iso_volatile_store8/16/32/64`内部函数显式执行不受编译器优化约束的内存访问。 编译器无法删除、合成或更改这些操作的相对顺序。 但是，它不会生成隐式硬件内存障碍。 因此，硬件仍可能对跨多个线程的可观察内存访问进行重新排序。 更确切地说，这些内在函数等效于以下表达式，这些表达式在 **/volatile：iso**下编译。

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

请注意内部函数采用易失性指针来适应易失性变量。 但是，没有要求或建议使用易失性指针作为参数。 如果使用常规非易失性类型，则这些操作的语义完全相同。

有关 **/volatile：iso**命令行参数的详细信息，请参阅[/volatile（易失性关键字解释）。](../build/reference/volatile-volatile-keyword-interpretation.md)

## <a name="arm64-support-for-intrinsics-from-other-architectures"></a><a name="I"></a>ARM64 支持其他体系结构的固有产品

下表列出了 ARM64 平台上支持的其他体系结构的固有函数。 如果 ARM64 上的内在行为不同于其他硬件体系结构上的行为，则请注意其他详细信息。

|函数名称|函数原型|
|-------------------|------------------------|
|__assume|void __assume(int)|
|__code_seg|空__code_seg（康斯特字符\*）|
|__debugbreak|无效__cdecl_debugbreak（\_空）|
|__fastfail|__declspec（无返回）无效\__fastfail（无符号int）|
|__nop|void __nop(void)|
|__yield|无效__yield（无效）**注意：** 在 ARM64 平台上，此功能生成 YIELD 指令。 此指令指示线程正在执行可能暂时暂停执行的任务（例如，旋转锁），而不会对程序产生负面影响。 它使 CPU 能够在执行周期内执行其他任务，否则这些任务会浪费。|
|_AddressOfReturnAddress|空\*_AddressOfReturnAddress（空）|
|_BitScanForward|无符号字符_BitScanForward（未签名的长\*_Index，未签名长_Mask）|
|_BitScanForward64|无符号字符_BitScanForward64（未签名长\*_Index，无符号__int64_Mask）|
|_BitScanReverse|无符号字符_BitScanReverse（无符号长\*_Index，无符号长_Mask）|
|_BitScanReverse64|无符号字符_BitScanReverse64（未签名的长\*_Index，无符号__int64_Mask）|
|_bittest|无符号字符_bittest（长孔\*，长）|
|_bittest64|无符号字符\*_bittest64（__int64，__int64）|
|_bittestandcomplement|无符号字符_bittestandcomplement（长\*，长）|
|_bittestandcomplement64|无符号字符_bittestandcomplement64（__int64，__int64） \*|
|_bittestandreset|无符号字符_bittestandreset（长\*，长）|
|_bittestandreset64|无符号字符_bittestandreset64（__int64，__int64） \*|
|_bittestandset|无符号字符_bittestandset（长\*，长）|
|_bittestandset64|无符号字符_bittestandset64（__int64，__int64） \*|
|_byteswap_uint64|未签名__int64_cdecl_byteswap_uint64（\_未签名\__int64）|
|_byteswap_ulong|unsigned long __cdecl _byteswap_ulong(unsigned long)|
|_byteswap_ushort|unsigned short __cdecl _byteswap_ushort(unsigned short)|
|_disable|无效__cdecl_disable（无效）**注意：** 在ARM64平台上，此功能生成指令`MSR DAIFCLR,#2`;它只能作为一种内在的。|
|_enable|空__cdecl_enable（无效）**注意：** 在ARM64平台上，此功能生成指令`MSR DAIFSET,#2`;它只能作为一种内在的。|
|_lrotl|unsigned long __cdecl _lrotl(unsigned long, int)|
|_lrotr|unsigned long __cdecl _lrotr(unsigned long, int)|
|_ReadBarrier|void _ReadBarrier(void)|
|_ReadWriteBarrier|void _ReadWriteBarrier(void)|
|_ReturnAddress|空\*_ReturnAddress（空）|
|_rotl|unsigned int __cdecl _rotl(unsigned int _Value, int _Shift)|
|_rotl16|unsigned short _rotl16(unsigned short _Value, unsigned char _Shift)|
|_rotl64|未签名__int64_cdecl_rotl64（\_未签名\__int64_Value，_Shift）|
|_rotl8|unsigned char _rotl8(unsigned char _Value, unsigned char _Shift)|
|_rotr|unsigned int __cdecl _rotr(unsigned int _Value, int _Shift)|
|_rotr16|unsigned short _rotr16(unsigned short _Value, unsigned char _Shift)|
|_rotr64|未签名__int64_cdecl_rotr64（\_未签名\__int64_Value，_Shift）|
|_rotr8|unsigned char _rotr8(unsigned char _Value, unsigned char _Shift)|
|_setjmpex|int __cdecl _setjmpex(jmp_buf)|
|_WriteBarrier|void _WriteBarrier(void)|

[[返回顶部](#top)]

## <a name="interlocked-intrinsics"></a>互锁内部

互锁内部函数是用于执行原子读取-修改-写入操作的一组内部函数。 其中一些互锁内部函数通用于所有平台。 它们在此处单独列出，因为存在大量。 因为它们的定义大多是多余的，因此更容易从一般角度考虑它们。 它们的名称可用于派生确切行为。

下表总结了 ARM64 对非位测试互锁内部项的支持。 表中的每个单元格都对应一个名称，这些名称的派生方式是将该行的最左侧单元格中的操作名和该列的最上面单元格中的类型名附加到 `_Interlocked`。 例如，`Xor`行和`8`列交集处的单元格对应于`_InterlockedXor8`并完全支持。 大部分受支持的函数提供以下可选后缀：`_acq`、`_rel` 和 `_nf`。 `_acq` 后缀表示“获取”语义，而 `_rel` 后缀表示“发布”语义。 或`_nf`"无栅栏"后缀是 ARM 和 ARM64 独有的，在下一节中将对此进行讨论。

||8|16|32|64|128|P|
|-|-------|--------|--------|--------|-------|-------|
|添加|None|None|完全|完全|None|None|
|And|完全|完全|完全|完全|None|None|
|CompareExchange|完全|完全|完全|完全|完全|完全|
|递减|None|完全|完全|完全|None|None|
|Exchange|完全|完全|完全|完全|None|完全|
|ExchangeAdd|完全|完全|完全|完全|None|None|
|增量|None|完全|完全|完全|None|None|
|Or|完全|完全|完全|完全|None|None|
|Xor|完全|完全|完全|完全|None|None|

注册表项：

- **完整**： 支持`_acq`普通`_rel`、、和`_nf`窗体。

- **无**： 不支持

### <a name="_nf-no-fence-suffix"></a><a name="nf_suffix"></a>_nf（无栅栏）后缀

或`_nf`"无栅栏"后缀表示操作不作为任何类型的内存屏障，与其他三种形式（普通、`_acq`和`_rel`）不同，它们都作为某种屏障运行。 `_nf`窗体的一个可能用途是维护一个统计计数器，该计数器同时由多个线程更新，但在多个线程执行时，其值未以其他方式使用。

### <a name="list-of-interlocked-intrinsics"></a>互锁内部函数列表

|函数名称|函数原型|
|-------------------|------------------------|
|_InterlockedAdd|长_InterlockedAdd（长_volatile\*长）|
|_InterlockedAdd64|__int64_InterlockedAdd64（_int64\_波动\*，_int64） \_|
|_InterlockedAdd64_acq|__int64_InterlockedAdd64_acq（_int64\_波动\*，_int64） \_|
|_InterlockedAdd64_nf|__int64_InterlockedAdd64_nf（_int64\_波动\*，_int64） \_|
|_InterlockedAdd64_rel|__int64_InterlockedAdd64_rel（_int64\_波动\*，_int64） \_|
|_InterlockedAdd_acq|长_InterlockedAdd_acq（长时间挥\*发性，长）|
|_InterlockedAdd_nf|长_InterlockedAdd_nf（长时间挥\*发性，长）|
|_InterlockedAdd_rel|长_InterlockedAdd_rel（长时间挥\*发性，长）|
|_InterlockedAnd|长_InterlockedAnd（长时间挥\*发性，长）|
|_InterlockedAnd16|短_InterlockedAnd16（短波动\*、短）|
|_InterlockedAnd16_acq|短_InterlockedAnd16_acq（短波动\*、短）|
|_InterlockedAnd16_nf|短_InterlockedAnd16_nf（短波动\*、短）|
|_InterlockedAnd16_rel|空_InterlockedAnd16_rel（短波动\*、短）|
|_InterlockedAnd64|__int64_InterlockedAnd64（_int64\_波动\*，_int64） \_|
|_InterlockedAnd64_acq|__int64_InterlockedAnd64_acq（_int64\_波动\*，_int64） \_|
|_InterlockedAnd64_nf|__int64_InterlockedAnd64_nf（_int64\_波动\*，_int64） \_|
|_InterlockedAnd64_rel|__int64_InterlockedAnd64_rel（_int64\_波动\*，_int64） \_|
|_InterlockedAnd8|字符_InterlockedAnd8 （字符\*易挥发 ， 字符）|
|_InterlockedAnd8_acq|字符_InterlockedAnd8_acq （字符\*易挥发 ， 字符）|
|_InterlockedAnd8_nf|字符_InterlockedAnd8_nf （字符\*易挥发 ， 字符）|
|_InterlockedAnd8_rel|字符_InterlockedAnd8_rel （字符\*易挥发 ， 字符）|
|_InterlockedAnd_acq|长_InterlockedAnd_acq（长挥\*发性，长）|
|_InterlockedAnd_nf|长_InterlockedAnd_nf（长时间挥\*发性，长）|
|_InterlockedAnd_rel|长_InterlockedAnd_rel（长时间挥\*发性，长）|
|_InterlockedCompareExchange|长__cdecl_InterlockedCompareExchange（长挥\*发、长、长）|
|_InterlockedCompareExchange_acq|长_InterlockedCompareExchange_acq（长挥\*发、长、长）|
|_InterlockedCompareExchange_nf|长_InterlockedCompareExchange_nf（长挥\*发、长、长）|
|_InterlockedCompareExchange_rel|长_InterlockedCompareExchange_rel（长挥\*发、长、长）|
|_InterlockedCompareExchange16|短_InterlockedCompareExchange16（短波动\*、短、短）|
|_InterlockedCompareExchange16_acq|短_InterlockedCompareExchange16_acq（短波动\*、短、短）|
|_InterlockedCompareExchange16_nf|短_InterlockedCompareExchange16_nf（短波动\*、短、短）|
|_InterlockedCompareExchange16_rel|短_InterlockedCompareExchange16_rel（短波动\*、短、短）|
|_InterlockedCompareExchange64|__int64_InterlockedCompareExchange64（_int64\_波动\*、_int64、_int64） \_ \_|
|_InterlockedCompareExchange64_acq|__int64_InterlockedCompareExchange64_acq（_int64\_波动\*、_int64、_int64） \_ \_|
|_InterlockedCompareExchange64_nf|__int64_InterlockedCompareExchange64_nf（_int64\_波动\*、_int64、_int64） \_ \_|
|_InterlockedCompareExchange64_rel|__int64_InterlockedCompareExchange64_rel（_int64\_波动\*、_int64、_int64） \_ \_|
|_InterlockedCompareExchange8|字符_InterlockedCompareExchange8 （字符\*易挥发， 字符， 字符）|
|_InterlockedCompareExchange8_acq|字符_InterlockedCompareExchange8_acq （字符\*易挥发， 字符， 字符）|
|_InterlockedCompareExchange8_nf|字符_InterlockedCompareExchange8_nf（字符挥\*发性，字符，字符）|
|_InterlockedCompareExchange8_rel|字符_InterlockedCompareExchange8_rel（字符挥\*发性，字符，字符）|
|_InterlockedCompareExchangePointer|空\*_InterlockedCompareExchangePointer（空\*挥\*发、\*空隙\*、空）|
|_InterlockedCompareExchangePointer_acq|空\*_InterlockedCompareExchangePointer_acq（空\*挥\*发、\*空隙\*、空）|
|_InterlockedCompareExchangePointer_nf|空\*_InterlockedCompareExchangePointer_nf（空\*挥\*发、\*空隙\*、空）|
|_InterlockedCompareExchangePointer_rel|空\*_InterlockedCompareExchangePointer_rel（空\*挥\*发、\*空隙\*、空）|
|_InterlockedCompareExchange128|\_无符号字符_InterlockedCompareExchange128（_int64volatile \* _Destination、_int64_ExchangeHigh、_int64_ExchangeLow、_int64_ComparandResult） \_ \_ \_ \*|
|_InterlockedCompareExchange128_acq|\_无符号字符_InterlockedCompareExchange128_acq（_int64volatile \* _Destination、_int64_ExchangeHigh、_int64_ExchangeLow、_int64_ComparandResult） \_ \_ \_ \*|
|_InterlockedCompareExchange128_nf|无符号字符_InterlockedCompareExchange128_nf（_int64\_易\*变_Destination、_int64_ExchangeHigh、_int64_ExchangeLow、_int64_ComparandResult） \_ \_ \_ \*|
|_InterlockedCompareExchange128_rel|\_无符号字符_InterlockedCompareExchange128_rel（_int64volatile \* _Destination、_int64_ExchangeHigh、_int64_ExchangeLow、_int64_ComparandResult） \_ \_ \_ \*|
|_InterlockedDecrement|长__cdecl_InterlockedDecrement（长时间挥\*发）|
|_InterlockedDecrement16|短_InterlockedDecrement16（短挥\*发性）|
|_InterlockedDecrement16_acq|短_InterlockedDecrement16_acq（短挥\*发性）|
|_InterlockedDecrement16_nf|短_InterlockedDecrement16_nf（短波动\*）|
|_InterlockedDecrement16_rel|短_InterlockedDecrement16_rel（短挥\*发性）|
|_InterlockedDecrement64|__int64_InterlockedDecrement64（_int64\_波动\*）|
|_InterlockedDecrement64_acq|__int64_InterlockedDecrement64_acq（_int64\_波动\*）|
|_InterlockedDecrement64_nf|__int64_InterlockedDecrement64_nf（_int64\_波动\*）|
|_InterlockedDecrement64_rel|__int64_InterlockedDecrement64_rel（_int64\_波动\*）|
|_InterlockedDecrement_acq|长_InterlockedDecrement_acq（长时间挥\*发）|
|_InterlockedDecrement_nf|长_InterlockedDecrement_nf（长时间挥\*发）|
|_InterlockedDecrement_rel|长_InterlockedDecrement_rel（长时间挥\*发）|
|_InterlockedExchange|长__cdecl_InterlockedExchange（长挥\*发_Target，长）|
|_InterlockedExchange_acq|长_InterlockedExchange_acq（长挥\*发_Target，长）|
|_InterlockedExchange_nf|长_InterlockedExchange_nf（长挥\*发_Target，长）|
|_InterlockedExchange_rel|长_InterlockedExchange_rel（长挥\*发_Target，长）|
|_InterlockedExchange16|短_InterlockedExchange16（短波动\*_Target，短）|
|_InterlockedExchange16_acq|短_InterlockedExchange16_acq（短波动\*_Target，短）|
|_InterlockedExchange16_nf|短_InterlockedExchange16_nf（短波动\*_Target，短）|
|_InterlockedExchange16_rel|短_InterlockedExchange16_rel（短波动\*_Target，短）|
|_InterlockedExchange64|__int64_InterlockedExchange64（_int64\_波动\*_Target，_int64） \_|
|_InterlockedExchange64_acq|__int64_InterlockedExchange64_acq（_int64\_波动\*_Target，_int64） \_|
|_InterlockedExchange64_nf|\___int64_InterlockedExchange64_nf（_int64_Target\*波动，_int64） \_|
|_InterlockedExchange64_rel|\___int64_InterlockedExchange64_rel（_int64_Target\*波动，_int64） \_|
|_InterlockedExchange8|字符_InterlockedExchange8（炭易\*挥发_Target，字符）|
|_InterlockedExchange8_acq|字符_InterlockedExchange8_acq（字符挥\*发性_Target，字符）|
|_InterlockedExchange8_nf|字符_InterlockedExchange8_nf（字符易\*失性_Target，字符）|
|_InterlockedExchange8_rel|字符_InterlockedExchange8_rel（炭易\*失性_Target，字符）|
|_InterlockedExchangeAdd|长__cdecl_InterlockedExchangeAdd（长时间挥\*发，长）|
|_InterlockedExchangeAdd16|短_InterlockedExchangeAdd16（短波动\*、短）|
|_InterlockedExchangeAdd16_acq|短_InterlockedExchangeAdd16_acq（短波动\*、短）|
|_InterlockedExchangeAdd16_nf|短_InterlockedExchangeAdd16_nf（短波动\*、短）|
|_InterlockedExchangeAdd16_rel|短_InterlockedExchangeAdd16_rel（短波动\*、短）|
|_InterlockedExchangeAdd64|__int64_InterlockedExchangeAdd64（_int64\_波动\*，_int64） \_|
|_InterlockedExchangeAdd64_acq|__int64_InterlockedExchangeAdd64_acq（_int64\_波动\*，_int64） \_|
|_InterlockedExchangeAdd64_nf|__int64_InterlockedExchangeAdd64_nf（_int64\_波动\*，_int64） \_|
|_InterlockedExchangeAdd64_rel|__int64_InterlockedExchangeAdd64_rel（_int64\_波动\*，_int64） \_|
|_InterlockedExchangeAdd8|字符_InterlockedExchangeAdd8 （字符\*易失性 ， 字符）|
|_InterlockedExchangeAdd8_acq|字符_InterlockedExchangeAdd8_acq （字符\*易挥发 ， 字符）|
|_InterlockedExchangeAdd8_nf|字符_InterlockedExchangeAdd8_nf （字符\*易挥发 ， 字符）|
|_InterlockedExchangeAdd8_rel|字符_InterlockedExchangeAdd8_rel （字符\*易挥发 ， 字符）|
|_InterlockedExchangeAdd_acq|长_InterlockedExchangeAdd_acq（长挥\*发性，长）|
|_InterlockedExchangeAdd_nf|长_InterlockedExchangeAdd_nf（长时间挥\*发性，长）|
|_InterlockedExchangeAdd_rel|长_InterlockedExchangeAdd_rel（长时间挥\*发性，长）|
|_InterlockedExchangePointer|空\*_InterlockedExchangePointer（空\*挥\*发_Target，\*空）|
|_InterlockedExchangePointer_acq|空\*_InterlockedExchangePointer_acq（空\*挥\*发_Target，\*空）|
|_InterlockedExchangePointer_nf|空\*_InterlockedExchangePointer_nf（空\*挥\*发_Target，\*空）|
|_InterlockedExchangePointer_rel|空\*_InterlockedExchangePointer_rel（真空\*挥\*发_Target，\*空）|
|_InterlockedIncrement|长__cdecl_InterlockedIncrement（长时间挥\*发）|
|_InterlockedIncrement16|短_InterlockedIncrement16（短波动\*）|
|_InterlockedIncrement16_acq|短_InterlockedIncrement16_acq（短挥\*发性）|
|_InterlockedIncrement16_nf|短_InterlockedIncrement16_nf（短波动\*）|
|_InterlockedIncrement16_rel|短_InterlockedIncrement16_rel（短挥\*发性）|
|_InterlockedIncrement64|__int64_InterlockedIncrement64（_int64\_波动\*）|
|_InterlockedIncrement64_acq|__int64_InterlockedIncrement64_acq（_int64\_波动\*）|
|_InterlockedIncrement64_nf|__int64_InterlockedIncrement64_nf（_int64\_波动\*）|
|_InterlockedIncrement64_rel|__int64_InterlockedIncrement64_rel（_int64\_波动\*）|
|_InterlockedIncrement_acq|长_InterlockedIncrement_acq（长时间挥\*发）|
|_InterlockedIncrement_nf|长_InterlockedIncrement_nf（长时间挥\*发）|
|_InterlockedIncrement_rel|长_InterlockedIncrement_rel（长时间挥\*发）|
|_InterlockedOr|长_InterlockedOr（长时间挥\*发性，长）|
|_InterlockedOr16|短_InterlockedOr16（短波动\*、短）|
|_InterlockedOr16_acq|短_InterlockedOr16_acq（短波动\*、短）|
|_InterlockedOr16_nf|短_InterlockedOr16_nf（短波动\*、短）|
|_InterlockedOr16_rel|短_InterlockedOr16_rel（短波动\*、短）|
|_InterlockedOr64|__int64_InterlockedOr64（_int64\_波动\*，_int64） \_|
|_InterlockedOr64_acq|__int64_InterlockedOr64_acq（_int64\_波动\*，_int64） \_|
|_InterlockedOr64_nf|__int64_InterlockedOr64_nf（_int64\_波动\*，_int64） \_|
|_InterlockedOr64_rel|__int64_InterlockedOr64_rel（_int64\_波动\*，_int64） \_|
|_InterlockedOr8|字符_InterlockedOr8 （字符\*易挥发 ， 字符）|
|_InterlockedOr8_acq|字符_InterlockedOr8_acq （字符\*易挥发 ， 字符）|
|_InterlockedOr8_nf|字符_InterlockedOr8_nf （字符\*易挥发 ， 字符）|
|_InterlockedOr8_rel|字符_InterlockedOr8_rel （字符\*易失性 ， 字符）|
|_InterlockedOr_acq|长_InterlockedOr_acq（长时间挥\*发性，长）|
|_InterlockedOr_nf|长_InterlockedOr_nf（长时间挥\*发性，长）|
|_InterlockedOr_rel|长_InterlockedOr_rel（长时间挥\*发性，长）|
|_InterlockedXor|长_InterlockedXor（长时间挥\*发性，长）|
|_InterlockedXor16|短_InterlockedXor16（短波动\*、短）|
|_InterlockedXor16_acq|空_InterlockedXor16_acq（短波动\*、短）|
|_InterlockedXor16_nf|短_InterlockedXor16_nf（短波动\*、短）|
|_InterlockedXor16_rel|短_InterlockedXor16_rel（短波动\*、短）|
|_InterlockedXor64|__int64_InterlockedXor64（_int64\_波动\*，_int64） \_|
|_InterlockedXor64_acq|__int64_InterlockedXor64_acq（_int64\_波动\*，_int64） \_|
|_InterlockedXor64_nf|__int64_InterlockedXor64_nf（_int64\_波动\*，_int64） \_|
|_InterlockedXor64_rel|__int64_InterlockedXor64_rel（_int64\_波动\*，_int64） \_|
|_InterlockedXor8|字符_InterlockedXor8 （字符\*易挥发 ， 字符）|
|_InterlockedXor8_acq|字符_InterlockedXor8_acq （字符\*易挥发 ， 字符）|
|_InterlockedXor8_nf|字符_InterlockedXor8_nf （字符\*易挥发 ， 字符）|
|_InterlockedXor8_rel|字符_InterlockedXor8_rel （字符\*易挥发 ， 字符）|
|_InterlockedXor_acq|长_InterlockedXor_acq（长时间挥\*发性，长）|
|_InterlockedXor_nf|长_InterlockedXor_nf（长时间挥\*发性，长）|
|_InterlockedXor_rel|长_InterlockedXor_rel（长时间挥\*发性，长）|

[[返回顶部](#top)]

### <a name="_interlockedbittest-intrinsics"></a>_interlockedbittest内在

纯联锁位测试内部函数是所有平台都通用的。 ARM64`_acq`添加了`_rel`，`_nf`和变体，它们只是修改操作的屏障语义，如本文前面[_nf（无栅栏）后缀](#nf_suffix)中所述。

|函数名称|函数原型|
|-------------------|------------------------|
|_interlockedbittestandreset|无符号字符_interlockedbittestandreset（长时间易\*挥发，长）|
|_interlockedbittestandreset_acq|无符号字符_interlockedbittestandreset_acq（长时间易\*挥发，长）|
|_interlockedbittestandreset_nf|无符号字符_interlockedbittestandreset_nf（长时间易\*挥发，长）|
|_interlockedbittestandreset_rel|无符号字符_interlockedbittestandreset_rel（长时间易\*挥发，长）|
|_interlockedbittestandreset64|无符号字符_interlockedbittestandreset64（__int64\*易变，__int64）|
|_interlockedbittestandreset64_acq|无符号字符_interlockedbittestandreset64_acq （__int64\*易变，__int64）|
|_interlockedbittestandreset64_nf|无符号字符_interlockedbittestandreset64_nf（__int64易\*变，__int64）|
|_interlockedbittestandreset64_rel|无符号字符_interlockedbittestandreset64_rel（__int64\*易变，__int64）|
|_interlockedbittestandset|无符号字符_interlockedbittestandset（长时间易\*挥发，长）|
|_interlockedbittestandset_acq|无符号字符_interlockedbittestandset_acq（长时间易\*挥发，长）|
|_interlockedbittestandset_nf|无符号字符_interlockedbittestandset_nf（长时间易\*挥发，长）|
|_interlockedbittestandset_rel|无符号字符_interlockedbittestandset_rel（长时间易\*挥发，长）|
|_interlockedbittestandset64|无符号字符_interlockedbittestandset64（__int64\*易变，__int64）|
|_interlockedbittestandset64_acq|无符号字符_interlockedbittestandset64_acq（__int64易\*变，__int64）|
|_interlockedbittestandset64_nf|无符号字符_interlockedbittestandset64_nf（__int64易\*变，__int64）|
|_interlockedbittestandset64_rel|无符号字符_interlockedbittestandset64_rel（__int64易\*变，__int64）|

[[返回顶部](#top)]

## <a name="see-also"></a>另请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[ARM 内部函数](arm-intrinsics.md)\
[ARM 装配器参考](../assembler/arm/arm-assembler-reference.md)\
[C++语言参考](../cpp/cpp-language-reference.md)

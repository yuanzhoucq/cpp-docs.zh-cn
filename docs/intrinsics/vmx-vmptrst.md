---
title: __vmx_vmptrst
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmptrst
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
ms.openlocfilehash: a736a632c7f711ac8fdcc4d73eaf2bd341d0c978
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654228"
---
# <a name="vmxvmptrst"></a>__vmx_vmptrst

**Microsoft 专用**

将存储到指定地址处的当前虚拟机控件结构 (VMCS) 的指针。

## <a name="syntax"></a>语法

```
void __vmx_vmptrst( 
   unsigned __int64 *VmcsPhysicalAddress 
);
```

### <a name="parameters"></a>参数

*VmcsPhysicalAddress*<br/>
[in]存储当前 VMCS 指针地址。

## <a name="remarks"></a>备注

VMCS 指针是一个 64 位物理地址。

`__vmx_vmptrst` 函数等同于 `VMPTRST` 计算机指令。 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息，搜索"Intel 虚拟化技术规范的 IA-32 Intel 体系结构，"文档在文档数字 C97063 002 [Intel Corporation](https://software.intel.com/articles/intel-sdm)站点。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__vmx_vmptrst`|x86、x64|

**标头文件** \<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)
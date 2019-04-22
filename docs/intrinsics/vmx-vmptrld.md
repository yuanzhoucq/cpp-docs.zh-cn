---
title: __vmx_vmptrld
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmptrld
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
ms.openlocfilehash: e3d552720d454a4f22af368616b3953452c6db0e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59040418"
---
# <a name="vmxvmptrld"></a>__vmx_vmptrld

**Microsoft 专用**

从指定的地址加载到当前的虚拟机控件结构 (VMCS) 的指针。

## <a name="syntax"></a>语法

```
int __vmx_vmptrld(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>参数

*VmcsPhysicalAddress*<br/>
[in]在其中存储 VMCS 指针的地址。

## <a name="return-value"></a>返回值

0<br/>
操作成功。

1<br/>
操作失败，当前 VMCS 的 `VM-instruction error field` 中提供了扩展状态。

2<br/>
操作失败，无可用状态。

## <a name="remarks"></a>备注

VMCS 指针是一个 64 位物理地址。

`__vmx_vmptrld` 函数等同于 `VMPTRLD` 计算机指令。 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息，搜索"Intel 虚拟化技术规范的 IA-32 Intel 体系结构，"文档在文档数字 C97063 002 [Intel Corporation](https://software.intel.com/articles/intel-sdm)站点。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__vmx_vmptrld`|X64|

**标头文件** \<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)
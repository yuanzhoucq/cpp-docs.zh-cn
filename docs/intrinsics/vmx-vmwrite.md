---
title: __vmx_vmwrite
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmwrite
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
ms.openlocfilehash: e368a1f6be51d37cdfe7ef352fca69e987fed62d
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328560"
---
# <a name="vmxvmwrite"></a>__vmx_vmwrite

**Microsoft 专用**

将指定的值写入到当前的虚拟机控件结构 (VMCS) 中指定的字段。

## <a name="syntax"></a>语法

```
unsigned char __vmx_vmwrite(
   size_t Field,
   size_t FieldValue
);
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*字段*|[in]要写入的 VMCS 字段。|
|*FieldValue*|[in]要写入的 VMCS 字段的值。|

## <a name="return-value"></a>返回值

操作已成功为 0。

1 中提供了扩展状态，操作失败`VM-instruction error field`，当前 vmcs。

2 无可用状态，，操作失败。

## <a name="remarks"></a>备注

`__vmx_vmwrite` 函数等同于 `VMWRITE` 计算机指令。 值`Field`参数是 Intel 文档中所述的编码的字段索引。 有关详细信息，搜索"Intel 虚拟化技术规范的 IA-32 Intel 体系结构，"文档在文档数字 C97063 002 [Intel Corporation](https://software.intel.com/articles/intel-sdm)站点，并请查阅该附录 C文档。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__vmx_vmwrite`|X64|

**标头文件** \<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmread](../intrinsics/vmx-vmread.md)
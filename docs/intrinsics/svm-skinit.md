---
title: __svm_skinit
ms.date: 09/02/2019
f1_keywords:
- __svm_skinit
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
ms.openlocfilehash: 6657921d647a23bf027a5800702527951f7f6831
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219866"
---
# <a name="__svm_skinit"></a>__svm_skinit

**Microsoft 专用**

启动已验证的安全软件（例如虚拟机监视器）的加载。

## <a name="syntax"></a>语法

```C
void __svm_skinit(
   int block_address
);
```

### <a name="parameters"></a>参数

*block_address*\
64K 字节安全加载器块（SLB）的32位物理地址。

## <a name="remarks"></a>备注

`__svm_skinit` 函数等同于 `SKINIT` 计算机指令。 此函数是安全系统的一部分，该系统使用处理器和受信任的平台模块（TPM）来验证和加载受信任的软件（称为*安全内核*（SK））。 虚拟机监视器是一个安全内核的示例。 安全系统将验证在初始化过程中加载的程序组件。 它可以防止组件被中断、设备访问或其他程序（如果计算机是多处理器）篡改。

*Block_address*参数指定名为*安全加载器块*（SLB）的64k 内存块的物理地址。 SLB 包含名为*安全加载*程序的程序。 它为计算机建立操作环境，然后加载安全内核。

此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息，请搜索 "AMD64 体系结构程序员手册卷2：[AMD 公司](https://developer.amd.com/resources/developer-guides-manuals/)网站的系统编程 "。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__svm_skinit`|x86、x64|

**标头文件**\<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)

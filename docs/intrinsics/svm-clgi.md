---
title: __svm_clgi
ms.date: 09/02/2019
f1_keywords:
- __svm_clgi
helpviewer_keywords:
- CLGI instruction
- __svm_clgi intrinsic
ms.assetid: 6640f5ab-9472-46f9-a042-e15c4f1ff858
ms.openlocfilehash: 740c76e5dcc8f94b9257272624a6ad3c1f9726c1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219968"
---
# <a name="__svm_clgi"></a>__svm_clgi

**Microsoft 专用**

清除全局中断标志。

## <a name="syntax"></a>语法

```C
void __svm_clgi( void );
```

## <a name="remarks"></a>备注

`__svm_clgi` 函数等同于 `CLGI` 计算机指令。 全局中断标志确定微处理器是由于事件（如 i/o 完成、硬件温度警报或调试异常）而忽略、推迟还是处理中断。

此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息，请搜索 "AMD64 体系结构程序员手册卷2：[AMD 公司](https://developer.amd.com/resources/developer-guides-manuals/)网站的系统编程 "。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__svm_clgi`|x86、x64|

**标头文件**\<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[__svm_stgi](../intrinsics/svm-stgi.md)

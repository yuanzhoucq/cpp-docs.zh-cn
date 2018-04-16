---
title: "_get_FMA3_enable，_set_FMA3_enable |Microsoft 文档"
ms.custom: 
ms.date: 6/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _get_FMA3_enable
- _set_FMA3_enable
apilocation:
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
- math/_get_FMA3_enable
- math/_set_FMA3_enable
dev_langs:
- C++
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4875306575d58b1baf341a5ed3c2a919c995c704
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="getfma3enable-setfma3enable"></a>_get_FMA3_enable _set_FMA3_enable
获取或设置一个标志，用于指定是否先验数学浮点库函数针对 X64 编译的代码中使用 FMA3 说明平台。  
  
## <a name="syntax"></a>语法  
  
```  
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```  
  
### <a name="parameters"></a>参数
*flag*  
设置为 1 以启用 X64 上的先验数学浮点库函数的 FMA3 实现平台，或为 0，以使用不会使用 FMA3 指令的实现。
  
## <a name="return-value"></a>返回值  
如果启用先验数学浮点库函数的 FMA3 实现了一个非零值。 否则为零。  
  
## <a name="remarks"></a>备注  
使用`_set_FMA3_enable`函数以启用或禁用在 CRT 库中的先验数学浮点函数的 FMA3 指令的使用。 返回的值反映在使用更改后的实现。 如果 CPU 不支持 FMA3 说明，此函数不能启用它们在库中，并返回值为零。 使用`_get_FMA3_enable`以获取当前状态的库。 默认情况下，在 X64 平台，CRT 启动代码检测到 CPU 支持 FMA3 说明，以及启用或禁用库中的 FMA3 实现。
  
由于 FMA3 实现使用不同的算法，计算的结果中的细微差异可能会可观测对象时 FMA3 实现是启用还是禁用，或的计算机或者不支持 FMA3 之间。 有关详细信息，请参阅[浮点迁移问题](../../porting/floating-point-migration-issues.md)。

## <a name="requirements"></a>要求  
  
`_set_FMA3_enable`和`_get_FMA3_enable`函数才可用在 X64 版本的 CRT。  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_set_FMA3_enable` <br /><br /> `_get_FMA3_enable`| C：\<math.h><br /><br /> C + +: \<t h > 或\<h.h >|  
  
`_set_FMA3_enable` 和 `_get_FMA3_enable` 函数是 Microsoft 的特定函数。 有关兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
[浮点支持](../../c-runtime-library/floating-point-support.md)
[浮点迁移问题](../../porting/floating-point-migration-issues.md)  
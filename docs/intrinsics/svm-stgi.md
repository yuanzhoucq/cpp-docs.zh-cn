---
title: __svm_stgi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_stgi
dev_langs:
- C++
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba43b12377bd9df959434c1c38d80ed8220c818a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333331"
---
# <a name="svmstgi"></a>__svm_stgi
**Microsoft 专用**  
  
 设置全局中断标志。  
  
## <a name="syntax"></a>语法  
  
```  
void __svm_stgi(void);  
```  
  
## <a name="remarks"></a>备注  
 `__svm_stgi`函数等同于`STGI`计算机指令。 全局中断标志确定微处理器忽略、 推迟，或处理中断遇到 I/O 完成时，硬件温度警报或调试异常等事件。  
  
 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息，搜索文档中，"AMD64 体系结构程序员手动卷 2： 系统编程中，"在文档数 24593，修订 3.11， [AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746)站点。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__svm_stgi`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [__svm_clgi](../intrinsics/svm-clgi.md)
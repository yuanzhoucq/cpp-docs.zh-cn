---
title: __svm_invlpga |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_invlpga
dev_langs:
- C++
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77ada66d0478996eac30c8218793d962e8fcf7ca
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680083"
---
# <a name="svminvlpga"></a>__svm_invlpga
**Microsoft 专用**  
  
 使计算机的转换旁视缓冲中的地址映射条目。 参数指定的虚拟地址和要使之无效的页的地址空间标识符。  
  
## <a name="syntax"></a>语法  
  
```  
void __svm_invlpga(  
     void *Va,  
     int ASID);  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `Va`|要使之无效的页的虚拟地址。|  
|[in] `ASID`|地址空间标识符 (ASID) 页上，要使之无效。|  
  
## <a name="remarks"></a>备注  
 `__svm_invlpga`函数等同于`INVLPGA`计算机指令。 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息，搜索文档中，"AMD64 体系结构编程人员手动卷 2： 系统编程中，"文档数 24593，修订 3.11， [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)站点。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__svm_invlpga`|x86、x64|  
  
 **标头文件** \<intrin.h >  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)
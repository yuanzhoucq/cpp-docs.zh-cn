---
title: 部分 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- section_CPP
- vc-pragma.section
dev_langs:
- C++
helpviewer_keywords:
- pragmas, section
- section pragma
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8d113c10ea8370a46560ba8668546c74b19c6f8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="section"></a>section
在 .obj 文件中创建一个节。  
  
## <a name="syntax"></a>语法  
  
```  
  
#pragma section( "section-name" [, attributes] )  
```  
  
## <a name="remarks"></a>备注  
 这些术语的含义*段*和*部分*是可互换的本主题。  
  
 一旦节被定义，它将对编译的其余部分保持有效。 但是，你必须使用[__declspec （allocate)](../cpp/allocate.md)或执行任何操作将放在节。  
  
 *节名称*是必需的参数将节的名称。 该名称不得与任何标准节名称发生冲突。 请参阅[/部分](../build/reference/section-specify-section-attributes.md)的创建部分时不应使用的名称列表。  
  
 `attributes` 是一个可选参数，包括要分配给该节的一个或多个逗号分隔的特性。 可能的 `attributes` 为：  
  
 **read**  
 允许对数据进行读取操作。  
  
 **write**  
 允许对数据进行写入操作。  
  
 **execute**  
 允许执行代码。  
  
 **shared**  
 在所有加载图像的进程之间共享该节。  
  
 **nopage**  
 将该节标记为不可分页：对于 Win32 设备驱动程序很有用。  
  
 **nocache**  
 将该节标记为不可缓存：对于 Win32 设备驱动程序很有用。  
  
 **discard**  
 将该节标记为可丢弃；对于 Win32 设备驱动程序很有用。  
  
 **remove**  
 将节标记为非内存驻留;虚拟设备驱动程序 (V*x*D) 仅。  
  
 如果不指定特性，则该节将具有读写特性。  
  
## <a name="example"></a>示例  
 在下面的示例中，第一个指令标识节及其特性。 不会将整数 `j` 放置到 `mysec` 中，因为它不是使用 `__declspec(allocate)` 声明的；`j` 将进入数据节。 整数 `i` 将进入 `mysec` 作为其 `__declspec(allocate)` 存储类特性的结果。  
  
```  
// pragma_section.cpp  
#pragma section("mysec",read,write)  
int j = 0;  
  
__declspec(allocate("mysec"))  
int i = 0;  
  
int main(){}  
```  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
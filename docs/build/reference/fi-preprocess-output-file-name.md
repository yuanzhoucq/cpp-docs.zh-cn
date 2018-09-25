---
title: -Fi （预处理输出文件名） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Fi
dev_langs:
- C++
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f69a4ab16956924e3bcfd785c6a86c7ac238b36
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431549"
---
# <a name="fi-preprocess-output-file-name"></a>/Fi（预处理输出文件名）

指定的输出文件的名称[/P （预处理到文件）](../../build/reference/p-preprocess-to-a-file.md)编译器选项将预处理的输出。

## <a name="syntax"></a>语法

```
/Fipathname
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`pathname`|由生成的名称和输出文件的路径 **/P**编译器选项。|

## <a name="remarks"></a>备注

使用 **/Fi**编译器选项结合 **/P**编译器选项。

如果您仅指定一个路径的`pathname`参数，该源代码文件的基名称用作预处理的输出文件的基名称。 `pathname`参数不需要特定文件扩展名。 但是，如果未指定文件扩展名，则使用".i"的扩展。

## <a name="example"></a>示例

下面的命令行对 PROGRAM.cpp 进行预处理，保留注释，添加[#line](../../preprocessor/hash-line-directive-c-cpp.md)指令，并将结果写入到 MYPROCESS.i 文件。

```
CL /P /FiMYPROCESS.I PROGRAM.CPP
```

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[/P（预处理到文件）](../../build/reference/p-preprocess-to-a-file.md)<br/>
[指定路径名](../../build/reference/specifying-the-pathname.md)
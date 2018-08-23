---
title: 模板 ref 类 (C + + /cli CX) |Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: a24d5f45-8dbb-4540-958f-c76c90d8ed93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fb322ae641a1821ed8434e0ea197acf752698e6
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592615"
---
# <a name="template-ref-classes-ccx"></a>模板 ref 类 (C++/CX)
C++ 模板没有发布到元数据，因此你的程序中不能具有公共或受保护的可访问性。 当然，你可在程序内部使用标准 C++ 模板。 此外，你可将私有 ref 类定义为模板，并可将显式专用模板 ref 类声明为公共 ref 类中的私有成员。  
  
## <a name="authoring-ref-class-templates"></a>创作 ref 类模板  
 下面的示例演示如何将私有 ref 类声明为模板，如何声明标准 C++ 模板，以及如何将二者同时声明为公共 ref 类中的成员。 请注意，标准 c + + 模板可专用的 Windows 运行时类型，在此种情况下 platform:: string ^。  
  
 [!code-cpp[cx_templates#01](../cppcx/codesnippet/CPP/templatedemo/class1.h#01)]  
  
## <a name="see-also"></a>请参阅  
 [类型系统 (C++/CX)](../cppcx/type-system-c-cx.md)   
 [Visual c + + 语言参考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空间参考](../cppcx/namespaces-reference-c-cx.md)
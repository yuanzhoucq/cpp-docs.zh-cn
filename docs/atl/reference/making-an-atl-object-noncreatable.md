---
title: 使 ATL 对象不可创建
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.objects
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
ms.openlocfilehash: 966c7c1e42cd707726a8ca65bb80914c29ad582e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62200141"
---
# <a name="making-an-atl-object-noncreatable"></a>使 ATL 对象不可创建

您可以更改基于 ATL 的 COM 对象的属性，以便客户端不能直接创建该对象。 在这种情况下，对象会被另一个对象上返回通过方法调用而不直接创建。

## <a name="to-make-an-object-noncreatable"></a>若要使对象不可创建

1. 删除[OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto)对象。 如果你想要注册的控件，但不可创建的对象，将替换为与 OBJECT_ENTRY_AUTO [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto)。

1. 添加[noncreatable](../../windows/noncreatable.md) .idl 文件中组件类的属性。 例如：

    ```
    [uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851),
    helpstring("MyObject"),
    noncreatable]
    coclass MyObject
    {
        [default] interface IMyInterface;
    }
    ```

## <a name="see-also"></a>请参阅

[ATL 项目向导](../../atl/reference/atl-project-wizard.md)<br/>
[Visual C++ 项目类型](../../build/reference/visual-cpp-project-types.md)<br/>
[使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[ATL COM 对象基础知识](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)

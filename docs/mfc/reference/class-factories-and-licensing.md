---
title: 类工厂和许可 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5cedcedce14ce2fa6638091f0785f0456dee9891
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419734"
---
# <a name="class-factories-and-licensing"></a>类工厂和许可

为了创建 OLE 控件的实例，容器应用程序调用了控件的类工厂的成员函数。 由于控件是实际 OLE 对象，类工厂将负责创建控件的实例。 每个 OLE 控件类必须有一个类工厂。

OLE 控件的另一个重要功能是强制使用许可证。 ControlWizard 可让您在控件项目的创建过程中包含授权。 有关控件授权的详细信息，请参阅文章[ActiveX 控件： 许可 ActiveX 控件](../../mfc/mfc-activex-controls-licensing-an-activex-control.md)。

下表列出了用于声明和实现控件的类工厂以及为控件授权的几个宏和函数。

### <a name="class-factories-and-licensing"></a>类工厂和许可

|||
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|声明 OLE 控件或属性页的类工厂。|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|实现控件的 `GetClassID` 函数并声明类工厂的实例。|
|[BEGIN_OLEFACTORY](#begin_olefactory)|开始任何授权函数的声明。|
|[END_OLEFACTORY](#end_olefactory)|结束任何授权函数的声明。|
|[AfxVerifyLicFile](#afxverifylicfile)|确认控件是否已获得在特定计算机上使用的授权。|

##  <a name="declare_olecreate_ex"></a>  DECLARE_OLECREATE_EX

声明类工厂和`GetClassID`控件类的成员函数。

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>参数

*class_name*<br/>
控件类的名称。

### <a name="remarks"></a>备注

不支持授权的控件的控件类标头文件中使用此宏。

请注意此宏提供下面的代码示例相同的目的：

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="implement_olecreate_ex"></a>  IMPLEMENT_OLECREATE_EX

实现控件的类工厂和[GetClassID](../../mfc/reference/colecontrol-class.md#getclassid)控件类的成员函数。

```
IMPLEMENT_OLECREATE_EX(
   class_name,
    external_name,
    l,
    w1,
    w2,
    b1,
    b2,
    b3,
    b4,
    b5,
    b6,
    b7,
    b8)
```

### <a name="parameters"></a>参数

*class_name*<br/>
控件属性页类的名称。

*external_name*<br/>
向应用程序公开的对象名称。

*l、 w1、 w2，b1、 b2、 b3、 b4、 b5、 b6、 b7、 b8*<br/>
类的 CLSID 的组件。 有关这些参数的详细信息，请参阅备注[IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate)。

### <a name="remarks"></a>备注

此宏必须出现在任何控件类，该类使用 DECLARE_OLECREATE_EX 宏或 BEGIN_OLEFACTORY 和 END_OLEFACTORY 宏的实现文件中。 外部名称是向其他应用程序公开 OLE 控件的标识符。 容器使用此名称请求此控件类的对象。

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="begin_olefactory"></a>  BEGIN_OLEFACTORY

开始你的控件类的标头文件中类工厂的声明。

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>参数

*class_name*<br/>
指定控件类这是其类工厂的名称。

### <a name="remarks"></a>备注

声明的授权函数的类工厂应 BEGIN_OLEFACTORY 后立即开始。

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="end_olefactory"></a>  END_OLEFACTORY

结束控件的类工厂的声明。

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>参数

*class_name*<br/>
这是其类工厂的控件类的名称。

### <a name="requirements"></a>要求

  **标头**afxctl.h

##  <a name="afxverifylicfile"></a>  AfxVerifyLicFile

调用此函数可验证由命名许可证文件`pszLicFileName`对 OLE 控件有效。

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>参数

*hInstance*<br/>
与授权控件关联的 DLL 的实例句柄。

*pszLicFileName*<br/>
指向包含许可证文件名的以 null 结尾的字符字符串。

*pszLicFileContents*<br/>
为必须匹配在许可证文件的开头找到序列的字节序列的点。

*cch*<br/>
中的字符数*pszLicFileContents*。

### <a name="return-value"></a>返回值

非零，如果许可证文件存在，并且开头中的字符序列*pszLicFileContents*; 否则为 0。

### <a name="remarks"></a>备注

如果*cch*为-1，此函数使用：

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>要求

  **标头**afxctl.h

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

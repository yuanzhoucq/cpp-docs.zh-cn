---
title: 类工厂和许可
ms.date: 11/04/2016
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
ms.openlocfilehash: 18d86122e57af056a50a4d94bac89d65a7b71c7d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855707"
---
# <a name="class-factories-and-licensing"></a>类工厂和许可

为了创建 OLE 控件的实例，容器应用程序调用了控件的类工厂的成员函数。 由于控件是实际 OLE 对象，类工厂将负责创建控件的实例。 每个 OLE 控件类必须有一个类工厂。

OLE 控件的另一个重要功能是强制使用许可证。 ControlWizard 可让您在控件项目的创建过程中包含授权。 有关控制授权的详细信息，请参阅文章[Activex 控件：授权 Activex 控件](../../mfc/mfc-activex-controls-licensing-an-activex-control.md)。

下表列出了用于声明和实现控件的类工厂以及为控件授权的几个宏和函数。

### <a name="class-factories-and-licensing"></a>类工厂和许可

|||
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|声明 OLE 控件或属性页的类工厂。|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|实现控件的 `GetClassID` 函数并声明类工厂的实例。|
|[BEGIN_OLEFACTORY](#begin_olefactory)|开始任何授权函数的声明。|
|[END_OLEFACTORY](#end_olefactory)|结束任何授权函数的声明。|
|[AfxVerifyLicFile](#afxverifylicfile)|确认控件是否已获得在特定计算机上使用的授权。|

##  <a name="declare_olecreate_ex"></a>DECLARE_OLECREATE_EX

声明类工厂和控件类的 `GetClassID` 成员函数。

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>parameters

*class_name*<br/>
控件类的名称。

### <a name="remarks"></a>备注

对于不支持授权的控件，请在控件类头文件中使用此宏。

请注意，此宏的作用与下面的代码示例相同：

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>要求

  **标头**afxctl。h

##  <a name="implement_olecreate_ex"></a>IMPLEMENT_OLECREATE_EX

实现控件的类工厂和控件类的[GetClassID](../../mfc/reference/colecontrol-class.md#getclassid)成员函数。

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

### <a name="parameters"></a>parameters

*class_name*<br/>
控件属性页类的名称。

*external_name*<br/>
向应用程序公开的对象名称。

*l，w1，w2，b1，b2，b3，b4，b5，b6，b7，b8*<br/>
类的 CLSID 的组件。 有关这些参数的详细信息，请参阅[IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate)的备注。

### <a name="remarks"></a>备注

此宏必须出现在使用 DECLARE_OLECREATE_EX 宏或 BEGIN_OLEFACTORY 和 END_OLEFACTORY 宏的任何控件类的实现文件中。 外部名称是向其他应用程序公开的 OLE 控件的标识符。 容器使用此名称来请求此控件类的对象。

### <a name="requirements"></a>要求

  **标头**afxctl。h

##  <a name="begin_olefactory"></a>BEGIN_OLEFACTORY

开始在控件类的标头文件中声明类工厂。

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>parameters

*class_name*<br/>
指定类工厂为的控件类的名称。

### <a name="remarks"></a>备注

类工厂授权函数的声明应在 BEGIN_OLEFACTORY 后立即开始。

### <a name="requirements"></a>要求

  **标头**afxctl。h

##  <a name="end_olefactory"></a>END_OLEFACTORY

结束控件的类工厂的声明。

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>parameters

*class_name*<br/>
其类工厂为的控件类的名称。

### <a name="requirements"></a>要求

  **标头**afxctl。h

##  <a name="afxverifylicfile"></a>AfxVerifyLicFile

调用此函数可验证 `pszLicFileName` 命名的许可证文件对 OLE 控件是否有效。

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>parameters

*hInstance*<br/>
与已授权控件关联的 DLL 的实例句柄。

*pszLicFileName*<br/>
指向以 null 结尾的字符串，该字符串包含许可证文件名。

*pszLicFileContents*<br/>
指向一个字节序列，该序列序列必须与许可证文件的开头处找到的序列匹配。

*cch*<br/>
*PszLicFileContents*中的字符数。

### <a name="return-value"></a>返回值

如果许可证文件存在并以*pszLicFileContents*中的字符序列开头，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果*cch*为-1，则此函数使用：

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>要求

  **标头**afxctl。h

## <a name="see-also"></a>另请参阅

[宏和全局](../../mfc/reference/mfc-macros-and-globals.md)

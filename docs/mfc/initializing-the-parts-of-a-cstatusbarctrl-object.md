---
title: 初始化 CStatusBarCtrl 对象的组成部分
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
ms.openlocfilehash: c813ef53f94fb773b62f102a484eed2be859772e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662158"
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>初始化 CStatusBarCtrl 对象的组成部分

默认情况下，状态栏使用独立的窗格显示状态信息。 这些窗格（也称为部件）可包含文本字符串、图标或两者。

使用[SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts)若要定义部件的数量和长度，状态栏将具有。 创建状态栏的部件后，请调用[SetText](../mfc/reference/cstatusbarctrl-class.md#settext)并[SetIcon](../mfc/reference/cstatusbarctrl-class.md#seticon)若要设置的文本或图标状态栏的特定部分。 成功设置部件后，控件会自动重绘。

以下示例初始化具有四个窗格的现有 `CStatusBarCtrl` 对象 (`m_StatusBarCtrl`)，然后在第二个部件中设置一个图标 (IDI_ICON1) 和一些文本。

[!code-cpp[NVC_MFCControlLadenDialog#31](../mfc/codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]

有关如何设置模式的详细信息`CStatusBarCtrl`对象到简单，请参阅[设置 CStatusBarCtrl 对象的模式](../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md)。

## <a name="see-also"></a>请参阅

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)


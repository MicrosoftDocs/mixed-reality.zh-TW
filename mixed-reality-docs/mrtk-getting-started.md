---
title: MRTK 第2版入門
description: 適用于想要利用 MRTK 的新開發人員
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality、測試、混合現實工具組、MRTK 第2版、MRTK、工具、SDK、HoloLens、HoloLens 2
ms.openlocfilehash: 46a06b951ae9aa60259f70be3fa1e558e7ab8ab6
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438351"
---
# <a name="getting-started-with-mrtk-v2"></a>開始使用 MRTK v2

## <a name="mrtk-getting-started-guide"></a>MRTK 消費者入門指南
如需開始使用 MRTK V2 的詳細資訊，請參閱[MRTK 快速入門手冊](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)。

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>什麼是混合現實工具組（MRTK）？
MRTK 是一項令人驚奇的開放原始碼工具組，自 HoloLens 首次發行之後就已經存在，而不是我們的開發人員社區的困難工作。 過去3年來，我們聽取了開發人員社區的意見反應，並已建立 MRTK v2 來考慮最大的顧慮。  

Unity 的 MRTK v2 是混合實境應用程式的開放原始碼跨平台開發套件。  MRTK 第 2 版主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。 此專案的目標是減少建立混合實境應用程式的進入障礙，以及回饋伴著我們成長的社群。 

若要深入瞭解，請參閱[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)。

## <a name="new-with-mrtk-v2"></a>MRTK v2 的新版本
我們想要強調我們對這些平臺工具的承諾。  事實上，我們利用 MRTK 第2版來開發收件匣的經驗，例如安裝體驗（OOBE）和我們的混合現實學習應用程式。  您也可以預期新的 HoloLens 2 功能會先透過 MRTK 公開，因為我們認為這是在我們的平臺上進行開發的最佳方式。 

### <a name="modular"></a>採用
我們以模組化的方式建立了它，因此您不需要將每個工具組放在您的專案中。  這其實有幾個優點。  它可以讓您的專案大小變小，也更容易管理。  除此之外，因為它是使用可編寫腳本的物件所建立，而且是介面驅動的，所以您也可以取代自己所包含的元件，以支援其他服務、系統和平臺。

### <a name="cross-platform"></a>跨平台
說到其他平臺，它有跨平臺支援。  雖然這並不代表每個平臺都有現成的支援，但我們確保當您將組建目標切換至其他平臺時，沒有任何工具組程式碼會中斷。  模組化設計的健全性和擴充性，讓您能夠以良好的路徑來支援多個平臺，例如 ARCore、ARKit 和 OpenVR。

### <a name="performant"></a>性能
使用行動平臺時，我們會考慮到效能。  這是非常重要的，我們想要確保工具不會對您工作。

## <a name="see-also"></a>請參閱
* [MRTK 入門指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [MRTK 檔首頁](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [安裝工具](install-the-tools.md)
* [從 HTK/MRTK 移植到 MRTK 第2版](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)

---
title: 深度相機白皮書-ISSCC 2018
description: 討論適用於 Azure 和 HoloLens 的下一個版本，在專案 Kinect 利用深度觀景窗的技術白皮書。
author: mattzmsft
ms.author: mazeller
ms.date: 7/5/2018
ms.topic: article
keywords: 事件、 iscc、 電腦視覺、 研究、 kinect、 hololens、 深度、 tof
ms.openlocfilehash: b692f9deeb7768e57ab6161b2c356a6610f18ed9
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594705"
---
# <a name="depth-camera-whitepaper---isscc-2018"></a><span data-ttu-id="0e9a5-104">深度相機白皮書-ISSCC 2018</span><span class="sxs-lookup"><span data-stu-id="0e9a5-104">Depth camera whitepaper - ISSCC 2018</span></span>

<span data-ttu-id="0e9a5-105">**標題：** 1Mpixel 65nm BSI 320 MHz 解調 TOF 映像的感應器與 3.5μm 全域快門像素和類比分類收納</span><span class="sxs-lookup"><span data-stu-id="0e9a5-105">**Title:** 1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning</span></span>

<span data-ttu-id="0e9a5-106">**參與者：** Cyrus S Bamji、 Swati Mehta、 Barry Thompson、 Tamer Elkhatib、 Stefan Wurster、 Onur Akkaya、 Andrew Payne、 John Godbaz、 Mike Fenton、 Vijay Rajasekaran、 Larry Prather、 Satya Nagaraja、 Vishali Mogallapu、 圖表 Snow、 豐富 McCauley、 Mustansir Mukadam，Iskender AgiShaun McCarthy、 Zhanping Xu、 Travis Perry、 William Qian、 Vei Han Chan、 Prabhu Adepu、 Gazi Ali、 Muneeb Ahmed、 Aditya Mukherjee、 Sheethal Nayak、 Dave Gampell、 Sunil Acharya，Lou Kordus Pat O'Connor</span><span class="sxs-lookup"><span data-stu-id="0e9a5-106">**Contributors:** Cyrus S Bamji, Swati Mehta, Barry Thompson, Tamer Elkhatib, Stefan Wurster, Onur Akkaya, Andrew Payne, John Godbaz, Mike Fenton, Vijay Rajasekaran, Larry Prather, Satya Nagaraja, Vishali Mogallapu, Dane Snow, Rich McCauley, Mustansir Mukadam, Iskender Agi, Shaun McCarthy, Zhanping Xu, Travis Perry, William Qian, Vei-Han Chan, Prabhu Adepu, Gazi Ali, Muneeb Ahmed, Aditya Mukherjee, Sheethal Nayak, Dave Gampell, Sunil Acharya, Lou Kordus, Pat O'Connor</span></span>

<span data-ttu-id="0e9a5-107">**於 ISSCC 2018，並在 ISSCC 度中發佈。技術。2018 年 2 月的文件。**</span><span class="sxs-lookup"><span data-stu-id="0e9a5-107">**Presented at ISSCC 2018 and published in ISSCC Deg. Tech. Papers, Feb 2018.**</span></span>

<span data-ttu-id="0e9a5-108">C.</span><span class="sxs-lookup"><span data-stu-id="0e9a5-108">C.</span></span> <span data-ttu-id="0e9a5-109">Bamji 要是，"1Mpixel 65nm BSI 320 MHz 解調 TOF 映像的感應器與 3.5μm 全域快門像素和類比分類收納 」 ISSCC 度。</span><span class="sxs-lookup"><span data-stu-id="0e9a5-109">Bamji et al., “1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning,” ISSCC Deg.</span></span> <span data-ttu-id="0e9a5-110">技術。</span><span class="sxs-lookup"><span data-stu-id="0e9a5-110">Tech.</span></span> <span data-ttu-id="0e9a5-111">白皮書、 pp.94-95，2018 年 2 月</span><span class="sxs-lookup"><span data-stu-id="0e9a5-111">Papers, pp. 94-95, Feb 2018.</span></span> <span data-ttu-id="0e9a5-112">IEEE 瀏覽連結： https://ieeexplore.ieee.org/document/8310200/</span><span class="sxs-lookup"><span data-stu-id="0e9a5-112">IEEE Explore Link: https://ieeexplore.ieee.org/document/8310200/</span></span>

<span data-ttu-id="0e9a5-113">© 2018 IEEE.</span><span class="sxs-lookup"><span data-stu-id="0e9a5-113">© 2018 IEEE.</span></span> <span data-ttu-id="0e9a5-114">允許個人使用這份資料。</span><span class="sxs-lookup"><span data-stu-id="0e9a5-114">Personal use of this material is permitted.</span></span> <span data-ttu-id="0e9a5-115">所有其他用法，在任何目前或未來的媒體，包括 reprinting/重新發行此資料用於廣告或促銷的用途，建立新集合的運作方式，針對轉售或重新發佈到伺服器或清單，請必須取得 IEEE 權限或重複使用這項工作中其他作品的任何受著作權保護的元件。</span><span class="sxs-lookup"><span data-stu-id="0e9a5-115">Permission from IEEE must be obtained for all other uses, in any current or future media, including reprinting/republishing this material for advertising or promotional purposes, creating new collective works, for resale or redistribution to servers or lists, or reuse of any copyrighted component of this work in other works.</span></span>

<span data-ttu-id="0e9a5-116">**白皮書：**</span><span class="sxs-lookup"><span data-stu-id="0e9a5-116">**Whitepaper:**</span></span><br>
<span data-ttu-id="0e9a5-117">![預覽的白皮書](images/depth-camera-isscc.PNG)</span><span class="sxs-lookup"><span data-stu-id="0e9a5-117">![Preview of whitepaper](images/depth-camera-isscc.PNG)</span></span><br>
[<span data-ttu-id="0e9a5-118">下載深度相機白皮書</span><span class="sxs-lookup"><span data-stu-id="0e9a5-118">Download depth camera whitepaper</span></span>](images/Depth-Camera-ISSCC-2018.pdf)

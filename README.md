# Botright v0.3

## Install it from PyPI

```bash
pip install botright
playwright install
```

---

## Usage

### Botright is currently only available in async mode.
### It is fully plugable with your existing playwright code. You only have to change your browser initialization!

```py
import asyncio

import botright


async def main():
    botright_client = await botright.Botright()
    browser = await botright_client.new_browser()
    page = await browser.new_page()

    # Continue by using the Page
    await page.goto("https://google.com")

    await botright_client.close()

if __name__ == "__main__":
    asyncio.run(main())
```

Read the [Documentation](https://github.com/Vinyzu/Botright/blob/main/docs/index.rst)

---

## Browser Stealth

Botright uses a vast amount of techniques to hide its functionality as a bot from websites.
To enhance stealth, since Version 0.3, it uses a real Chromium-based browser from the local machine to start up a botted browser.
For best stealth, you want to install [Ungoogled Chromium](https://ungoogled-software.github.io/ungoogled-chromium-binaries/)
Furthermore, it uses scraped and AI-enhanced (bayesian network based) fingerprints to build up a fake browser fingerprint and to deceive website into thinking it is legit.


| Test                                                                                                | Status | Score                                                      |
|-----------------------------------------------------------------------------------------------------|-------|------------------------------------------------------------|
| **reCaptcha Score**                                                                                 |   ✔️ | 0.9                                                        |
| => [nopecha.com](https://nopecha.com/demo/recaptcha#v3)                                             |   ✔️ | 0.9                                                        |
| => [recaptcha-demo.appspot.com](https://recaptcha-demo.appspot.com/recaptcha-v3-request-scores.php) |   ✔️ | 0.9                                                        |
| => [berstend.github.io](https://berstend.github.io/static/recaptcha/v3-programmatic.html)           |   ✔️ | 0.9                                                        |
| => [antcpt.com](https://antcpt.com/score_detector/)                                                 | ❌❓ | 0.1 (Detects Legitimate Browsers as Bad)                   |
| [**CreepJS**](https://abrahamjuliot.github.io/creepjs/)                                             |   ✔️ | ~56% (With Canvas Manipulation 9%)                         |
| **DataDome**                                                                                        |   ✔️ |                                                            |
| => [antoinevastel.com](https://antoinevastel.com/bots/datadome)                                     |   ✔️ |                                                            |
| => [datadome.co](https://datadome.co/bot-tester/)                                                   |   ✔️ |                                                            |
| **Imperva**                                                                                         | ✔️❓ | (Cant find approved Testing Sites)                         |
| => [ticketmaster.es](https://www.ticketmaster.es/)                                                  |   ✔️ |                                                            |
| **Cloudflare**                                                                                      |   ❌ |                                                            |
| => [Turnstile](https://nopecha.com/demo/turnstile)                                                  |   ❌ |                                                            |
| => [Interstitial](https://nopecha.com/demo/cloudflare)                                              |   ❌ |                                                            |
| [**SannySoft**](https://bot.sannysoft.com/)                                                         |   ✔️ |                                                            |
| [**Incolumitas**](https://bot.incolumitas.com/)                                                     |   ✔️ | 0.8-1.0                                                    |
| [**Fingerprint.com**](https://fingerprint.com/products/bot-detection/)                              |   ✔️ |                                                            |
| [**IpHey**](https://iphey.com/)                                                                     |   ✔️ |                                                            |
| [**BrowserScan**](https://browserscan.net/)                                                         |   ❓ | (Maybe caused by WebGL-disabling)                          |
| [**PixelScan**](https://pixelscan.net/)                                                             |   ❓ | (Platform Test Outdated & Maybe caused by WebGL-disabling) |


---

## Captcha Solving

Botright is able to solve a wide viarity of Captchas.
For Documentation of these functions visit [BotrightDocumentation](botright.md).

It uses Computer Vision/Artificial Intelligence and other Methods to solve these Captchas.

You dont need to pay for any Captcha Solving APIs and you can solve Captchas with just one simple function call.

Here all Captchas supported as of now:

|             Captcha Type             | Supported |            Solved By            | Success Rate |
|:------------------------------------:|:---------:|:-------------------------------:|--------------|
|              `hCaptcha`              |    ✔️    |       hcaptcha-challenger       | up to 90%    |
| `reCaptcha` Currently Not Available! |    ✔️    |      recaptcha-challenger       | 50%-80%      |
| `geeTestv3` Currently Not Available! |
|         v3 Intelligent Mode          |    ✔️    |     botrights stealthiness      | 100%         |
|          v3 Slider Captcha           |    ✔️    |        cv2.matchTemplate        | 100%         |
|           v3 Nine Captcha            |    ✔️    |         CLIP Detection          | 50%          |
|           v3 Icon Captcha            |    ✔️    | cv2.matchTemplate / SSIM / CLIP | 70%          |
|           v3 Space Captcha           |    ❌    |          Not solvable           | 0%           |
| `geeTestv4` Currently Not Available! |
|         v4 Intelligent Mode          |    ✔️    |     botrights stealthiness      | 100%         |
|          v4 Slider Captcha           |    ✔️    |        cv2.matchTemplate        | 100%         |
|          v4 GoBang Captcha           |    ✔️    |        Math Calculations        | 100%         |
|           v4 Icon Captcha            |    ✔️    | cv2.matchTemplate / SSIM / CLIP | 60%          |
|         v4 IconCrush Captcha         |    ✔️    |        Math Calculations        | 100%         |

## Development

Read the [CONTRIBUTING.md](https://github.com/Vinyzu/Botright/blob/main/CONTRIBUTING.md) file.

---

## Copyright and License
© [Vinyzu](https://github.com/Vinyzu/)

[GNU GPL](https://choosealicense.com/licenses/gpl-3.0/)

(Commercial Usage is allowed, but source, license and copyright has to made available. Botright does not provide and Liability or Warranty)

---

## Thanks to

[QIN2DIM](https://github.com/QIN2DIM/) (For his great AI work)

[MaxAndolini](https://github.com/MaxAndolini) (For shared knowledge of hCaptcha bypassing)

[CreativeProxies](https://creativeproxies.com) (For sponsoring me with Proxies)

---

![Version](https://img.shields.io/badge/Botright-v0.3-blue)
![License](https://img.shields.io/badge/License-GNU%20GPL-green)
![Python](https://img.shields.io/badge/Python-v3.x-lightgrey)

[![my-discord](https://img.shields.io/badge/My_Discord-000?style=for-the-badge&logo=google-chat&logoColor=blue)](https://discordapp.com/users/935224495126487150)
[![buy-me-a-coffee](https://img.shields.io/badge/Buy_Me_A_Coffee-000?style=for-the-badge&logo=ko-fi&logoColor=brown)](https://ko-fi.com/vinyzu)
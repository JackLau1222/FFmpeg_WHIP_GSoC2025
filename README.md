# GSoC 2025 FFmpeg WHIP

<div align='center' display='flex'>
    <img src="./gsoc.png" style="width: 50%; height: auto;">
</div>

<div align='center' display='flex'>
    <img src="./ffmpeg.png" style="width: 50%; height: auto;">
</div>

## Project Infomation:

### Project Name: [Implementation of WHIP (WebRTC-HTTP Ingestion Protocol) in FFmpeg](https://summerofcode.withgoogle.com/programs/2025/projects/CjXkqCQX)

### Mentor: Steven Liu, Jun Zhao

### Student: Jack Lau

---

## Description

This project aims to add WebRTC (Real-Time Communication) muxer that supports sub-second latency streaming according to the WHIP (WebRTC-HTTP ingestion protocol) specification.

Before GSoC, the initial [WHIP patch](https://github.com/ossrs/ffmpeg-webrtc/tree/patch/whip/v1) were written by Winlin and many other RTC developers.

My first GSoC work is to refactor and improve code until it can be merged into FFmpeg.

## What i did

- Refactor the openssl DTLS code and merge it into tls code
- Fix some bugs of whip and refactor it to make it more stable
- Add more features like NACK, RTX, DTLS active mode
- Implement dtls support for more ssl libs like gnutls, mbedtls.

## The current state

This WHIP muxer and openssl DTLS has been successfully merged into FFmpeg and released in FFmpeg 8.0 version

You could refer to the following introduction to test the WHIP,
https://github.com/ossrs/ffmpeg-webrtc/discussions/49

Then you'll find that it can achieve latency as low as 150ms:
![latency](./latency.png)

## What's left to do

- to make the more features like NACK, RTX, DTLS active mode be merged
- to make dtls support for multi ssl(gnutls, mbedtls) be merged.
- refactor the SDP logic to make it can directly utilize the sdp.c of FFmpeg.
- implment the multi-codec support(e.g. H265, AV1, VP9)
- maintaining the WHIP and DTLS code and add more features.

## What code got merged (or not) upstream

Merged:

- [The basic WHIP muxer and DTLS support](https://github.com/FFmpeg/FFmpeg/commit/167e343bbe75515a80db8ee72ffa0c607c944a00)
- [Many fixes and improvments](https://github.com/FFmpeg/FFmpeg/commits?author=JackLau1222&since=2025-06-01&until=2025-08-25)

Waiting for merge:
- NACK, RTX
- DTLS active mode
- DTLS for multi ssl(gnutls, mbedtls)

## Any challengs or important things i learned during the project

- When entering a new field, there are always many difficulties. At the beginning of this project, I not only had to study the WHIP-related standards, but also understand the existing code structure, FFmpeg’s framework design, the usage of OpenSSL APIs, and the challenges of multi-version compatibility. Being open-minded and frequently seeking guidance from my mentors greatly accelerated this process and even helped me avoid many detours.

- All roads lead to Rome — the solution one personally believes is correct may not necessarily be the optimal one. It’s important to consider the overall structure, rather than focusing only on the parts of the code related to oneself.

- For a foundational library like FFmpeg, code quality, stability, and performance are of the highest importance.I’ve learned a great deal from working on it — such as using bitwise operations to improve performance, writing code in compliance with international standards, and optimizing code structure for long-term maintainability.These lessons have contributed enormously to my growth as a programmer, in ways that are hard to fully put into words.

## Conclusion

As a newcomer to programming, I feel very fortunate to work alongside so many experienced developers and contribute together to open source. The excitement and sense of achievement when seeing my code merged upstream is truly unparalleled.

I would like to express my gratitude to my mentors Steven Liu and Jun Zhao, to Winlin as the initial author of WHIP, and to the many RTC developers and FFmpeg maintainers for their support and guidance.

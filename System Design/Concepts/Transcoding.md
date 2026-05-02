Video transcoding is the process of taking a video file or stream and converting it from one format to another. This is often necessary to ensure compatibility between devices or platforms. The process involves decoding the original video, processing it and then encoding it into the required format.

Transcoding is used for

* Ensuring compatibility between devices or platforms
* Reducing file size, if you are storing a huge collection of videos on a data lake, compressing it will save storage space and network throughput
* Improved Playback, some videos are most efficient for editing and playback.

Common transcoding tools include [HandBrake](https://handbrake.fr/), [FFmpeg](https://ffmpeg.org/) and [Adobe Media Encoder ](https://www.adobe.com/products/media-encoder.html)

### Adaptive Streaming

Transcoding is heavily used bny service providers such as Youtube and Netflix. When a creator uploads a video, these service providers compress these files, create multiple versions of the video with different resolutions and bitrates, this helps save network throughput and improves latency when providing the correct video resolution to the correct device.

### Device Compatibility

Some devices prefer different encodings then other, browsers on different operating systems on different mobile devices manufactured by different companies.

### DRM and Content Protection

Apply encryption to the video, useful for paid streaming services.

### Preview

Extract frames and generate previews for the video (Youtube does this).



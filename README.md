[![Build Status](https://travis-ci.org/dnault/libresample4j.svg?branch=main)](https://travis-ci.org/dnault/libresample4j)
[![LGPL 2.1](https://img.shields.io/badge/license-LGPL%202.1-blue.svg)](http://www.gnu.org/licenses/old-licenses/lgpl-2.1.en.html#SEC1)
![Java 1.5+](https://img.shields.io/badge/java-1.7+-lightgray.svg)

# libresample4j

Java port of Dominic Mazzoni's libresample 0.1.3, which is in turn based on Julius Smith's Resample 1.7 library.

There's no documentation for the Java port, but for the most part it's just like the C version which you can read about here:
    https://ccrma.stanford.edu/~jos/resample/Free_Resampling_Software.html

Also take a look at the C version's README which is bundled in the `libresample-0.1.3.tgz` archive.

## Example

```
int sampleRateIn = 16000;
int sampleRateOut = 48000;
Resampler resampler = new Resampler(sampleRateIn, sampleRateOut);

byte[] audioBytes; // or float[]
byte[] resampledBytes; // or float[]
while (...) { // Read audio data to audioBytes array
    resampledBytes = resampler.process(audioBytes, audioDataReader.isLastBatch());
    // lastBatch is needed to correctly form the end of the file
    // sourceDataLine.write(resampledBytes, 0, resampledBytes.length); // Play audio
}
```
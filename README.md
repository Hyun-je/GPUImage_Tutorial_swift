# Vision_Tutorial_swift



# Swift
### CIImage to UIImage ###
```swift
func convert(cmage:CIImage) -> UIImage
{       
    let context:CIContext = CIContext.init(options: nil)
    let cgImage:CGImage = context.createCGImage(cmage, from: cmage.extent)!        
    let image:UIImage = UIImage.init(cgImage: cgImage)        
    return image
}
```

# OpenCV

### PixelBuffer to Mat ###

```swift
CVPixelBufferLockBaseAddress(pixelBuffer, CVPixelBufferLockFlags.readOnly)

let pixelBufferRef  = CVPixelBufferGetBaseAddress(pixelBuffer)
let width     = CVPixelBufferGetWidth(pixelBuffer);
let height    = CVPixelBufferGetHeight(pixelBuffer);
```

```swift
cv::Mat inputMat = cv::Mat(height, width, CV_8UC4, (unsigned char *)inputImageBuffer);
```

```swift
CVPixelBufferUnlockBaseAddress(pixelBuffer, CVPixelBufferLockFlags.readOnly);
```

### Mat to NSData ###
```swift
[NSData dataWithBytes:grayMat.data length:grayMat.elemSize() * grayMat.total()];
```


# GPUImage
### UInt8 Array to UIImage ##

```swift
let width = 960
let height = 540

let nsData = NSData(bytes: data, length: data.count)
let dataProvider = CGDataProvider(data: nsData)!

let defaultRGBColorSpace = CGColorSpace.init(name: CGColorSpace.sRGB)!

let cgImage = CGImage(width:width, height:height,
                      bitsPerComponent:8, bitsPerPixel:32, bytesPerRow:4 * width,
                      space:defaultRGBColorSpace,
                      bitmapInfo:CGBitmapInfo(rawValue: CGImageAlphaInfo.noneSkipLast.rawValue),
                      provider:dataProvider, decode:nil, shouldInterpolate:false, intent:.defaultIntent)!

let uIimage = UIImage(cgImage: cgImage)
```


---
-api-id: M:Windows.Graphics.Imaging.BitmapFrame.GetThumbnailAsync
-api-type: winrt method
---

<!-- Method syntax
public Windows.Foundation.IAsyncOperation<Windows.Graphics.Imaging.ImageStream> GetThumbnailAsync()
-->

# Windows.Graphics.Imaging.BitmapFrame.GetThumbnailAsync

## -description
Asynchronously returns a stream containing the thumbnail image.

## -returns
Object that manages the asynchronous retrieval of the thumbnail data.

## -remarks
Many image formats, like JPEG and TIFF, allow a small sized thumbnail of the full image to be embedded within a frame. If the image does not contain a thumbnail, then this operation will fail with HRESULT [WINCODEC_ERR_CODECNOTHUMBNAIL](https://msdn.microsoft.com/library/1ded909c-311b-49e3-ba23-b22cd7a77bc6). If it exists, the EXIF orientation flag on the frame is automatically applied to the thumbnail before it is returned.

## -examples

## -see-also
